---
title: Configuració de proxy Squid amb servidor d'autenticació freeradius en Docker

description: En esta práctica montaremos una infraestructura, utilizando contenedores Docker, donde un navegador Firefox utilizará un proxy Squid para accedder a Internet, tanto http como https. Además se utilizará Freeradius como servidor de autenticación.
---

## Tasques a realitzar i detalls de la práctica

![](./img/squid_radius.png)


1. El secret compartit es *invent*
2. Com a contrasenya de root de la BBDD MySQL podeu posar la que més vos agrade
3. Heu d'omplir els ports a utilitzar per cada servici en el `docker-compose.yml`(son els ports per defecte)
4. Crear un usuari en el arxiu **clients.conf** de Freeradius.
5. A l'inici del fitxer **authorize** crear un usuari amb autenticació en text plà (la credencial serà el vostre nom i de contrasenya el cognonm)
6. Heu d'omplir l'arxiu **radius_config** de Squid.
7. Afegir una ACL (llista d'accés) que es cride `SSL_Ports` i que incloga el port 443.
8. Configurar Firefox per a utilitzar el proxy, tant http, com https.
9. Insertar un usuari en la BBDD `radius` des del contenidor de *freeradius*, en la taula `radcheck`. Els valors:
    
        username --> Omplir
        attribute --> "Cleartext-Password"
        op --> ":="
        value --> Omplir

10. Totes les comprovacions s'han de fer mostrant els logs

