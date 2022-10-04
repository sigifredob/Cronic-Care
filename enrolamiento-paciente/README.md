# Servicio **enrolamiento-paciente**



1. [Qué hace](#qué-hace)
1. [Qué necesita](#qué-necesita)
1. [Cargar procedimiento almacenado](#procedimiento-almacenado)
1. [Archivo de configuración](#archivo-configuracion)
1. [Como se usa](#cómo-se-usa)
1. [Dónde funciona](#dónde-funciona)
1. [Logs y properties](#logs-y-properties)


### Qué hace
---
- [X]  Enrolar paciente
    - [X]  Llamar Procedimiento Almacenado [`usp_post_crearPaciente`].


### Qué necesita
---
- Openjdk version 1.8.0_252
- Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)


### Cargar procedimiento almacenado
---
- Ejecutar archivo **usp_post_crearPaciente.sql** en la base de datos **CRONICARE**

**Bases de datos**

|Ambiente| Máquinas |
|--------|----------|
|Desarrollo|XX.XX.XX.XX|
|QA|YY.YY.YY.YY|
|Producción|ZZ.ZZ.ZZ.ZZ |

**NOTA**
Confirmar que las tablas **TABLA 1** y **TABLA 2** se encuentren en los diferentes servidores.


### Archivo de configuración
---
El archivo **enrolamiento-paciente.properties** se encuentra en **docs/recursos/configuraciones** de este repositorio
- Donde copiar
    - Copiar el archivo **enrolamiento-paciente.properties** en **/data/config/enrolamiento-paciente/** del servidor correspondiente. ver sección donde funciona. 
- Establecer valores a variables de configuración
    - **server.port:** Establecer el número del puerto por el cuál será expuesto el servicio por defecto se encuentra seteado el puerto **8016**
    - **spring.primarydatasource.jdbc-url:** Establecer la url JDBC. La base de datos siempre será **CRONICARE**, solo se debe establecer el servidor y el puerto. de la siguiente manera: **jdbc:sqlserver://{servidor}:{puerto};databaseName=CRONICARE**
    - **spring.primarydatasource.username:** Establecer nombre de usuario de la base de datos.
    - **spring.primarydatasource.password:** Establecer contraseña de usuario de la base de datos.


### Cómo se usa (Incluir todos los métodos)
----
#### Obtener enrolamiento del paciente

* **URL**

  http://`{host}`:`{port}`/v1/enrolamiento-paciente/{rut}

* **Method:**

  `GET`

* **Request Body**

    N/A

* **Respuesta Exitosa:**

  * **Código:** 200 <br />
    **Body:**
    ```json
    [
          {
        "primerNombre": "Juan",
        "segundoNombre": "Martín",
        "primerApellido": "Del",
        "segundoApellido": "Potro",
        "ID": 828323,
        "Rut": 12901663-3,
        "fechaEnrolamiento": "2021-12-31T00:00:00.000+0000"
     }
    ]
    ```
* **Respuesta No sé encontró paciente:**

  * **Código:** 404 No Found <br />
    **Body:** N/A

* **Respuesta Error:**

  * **Código:** 500 Internal Server Error <br />
    **Body:** N/A


* **Llamada de ejemplo:**

  ```bash
  curl -H "Accept: application/json" -H "Content-Type: application/json" http://xx.xx.xx.xx/v1/enrolamiento-paciente/12901663-3
  ```


### Dónde funciona

|Ambiente| Máquinas |
|--------|----------|
|Desarrollo|XX.XX.XX.XX|
|QA|YY.YY.YY.YY|
|Producción|ZZ.ZZ.ZZ.ZZ ||


### Logs y properties

* Log: `/log/cronicare/enrolamiento-paciente-out.log`
* Properties (ecosystem.config.js): `/data/backend/enrolamiento-paciente/ecosystem.config.js`
* Properties (afc-bck-afiliado-rentabilidad.properties): `/data/config/enrolamiento-paciente/enrolamiento-paciente.properties`


**NOTA**
Si las carpetas especificadas en **logs y properties** no se encuentran se deben crear.
