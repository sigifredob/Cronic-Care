Here is a simple flow chart:

```mermaid
sequenceDiagram
    par Rudy a Tirso
        Rudy->>Tirso: Favor ayudar a Cristian
    and Rudy a Cristian
        Rudy->>Cristian: Quiero esto para hoy
        par Cristian a Benjamin
            Cristian->>Benjamin: ¿Podemos hacer esto para hoy?
        and Cristian a Sigifredo
            Cristian->>Sigifredo: ¿Puedes ayudarnos hoy?
        end
    end
```
