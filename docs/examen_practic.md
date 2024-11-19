## Examen pràctic del primer trimestre (RA1 i RA2)

En primer lloc, baixem la imatge Docker que utilitzarem per a l'examen:

```console
docker pull br3baj3/examen_practic_1er:latest
```

I una vegada fet això, executem el contenidor amb el nom **examen_container**, en *background* i mapejant el port **8888** de la nostra pròpia màquina al 2222 del contenidor. Després comprovarem que el contenidor està corrent sense problemes:

```console
docker run --name examen_container -d -p 8888:2222 br3baj3/examen_practic_1er:latest

docker ps
```
# [Història de dos ciutats](https://www.filmaffinity.com/es/film229121.html)

Per a esta pràctica/examen, assumirem primer el paper d'un atacant/ciberdelincuent i despŕes el de l'administrador de sistemes que vol solucionar el problema.

## Atacant

Suposem que el atacant ha aconseguit unes credencials d'alguna forma no molt ética i les fa servir.

Haurem d'esperar 1 ó 2 minuts per a que finalitze la provisió del contenidor. Passat este temps podrem conectar-nos per SSH: 

```bash
ssh examen_practic@localhost -p8888
```
!!!info
    + **usuari**: examen_practic
  
    + **contrasenya**: examensad

En primer lloc, l'atacant vol facilitar-se la vida a l'hora de fer servir las credencials i conectar-se a la màquina d'una forma més còmoda.

!!!task "Tasca 1 - Conexió SSH amb claus"
    Crea un parell de claus i copia-les al server per a conectarte mitjançant clau pública. Comprova que funciona correctament.


Després d'una intensa auditoria, el ciberdelincuent ha descobert que la màquina té una vulnerabilitat del paquet <u>pkexec</u> molt crítica anomenada *Pwnkit* que permet a un usuari escalar privilegis i convertir-se en root.

!!!task "Tasca 2 - Explotació de la vulnerabilitat"
    Busca un exploit <u>en python</u> per a **pwnkit** i fes-lo servir a la màquina per a convertir-te en root.

El ciberdelincuent, aprofitant els seus poders de root, vol cobrir les seues empremtes i per tant, procurarà esborrar dels logs les línies que facin referència al login amb claus (el login original estava amb usuari/contrasenya i una altra cosa alçaría sospites). Per a fer això utilitzarà l'eina **vi** i <u>no</u> **nano**.

!!!task "Tasca 3 - Ocultació d'evidències"
    Busca entre els arxius del directori a on s'ubiquen tots els logs del sistema totes les línies que facin referència a l'usuari *examen_practic*. Entre eixes línies hi haurà algunes que facin referència al login *ssh* amb clau pública, que també pots filtrar si vols.

    Ara, amb l'eina *vi* obri l'arxiu d'on hagis d'esborrar les línies i esborra només les que mostren un login amb clau pública.

!!!tip "Consells"
    **Vi** és una eina un poc especial, alguns consells per a fer-lo servir:

      + Per pasar al mode d'inserció de text heu de prémer primer la tecla **i**
        + En este mode podeu escriure i esborar
      + Després d'escriure lo desitjat, heu d'eixir del mode d'inserció prement la tecla *ESC*
      + Fora del mode d'inserció de text podeu buscar paraules escrivint **/terme_a_buscar** (important la barra)
        + Per a buscar la següent coincidència, premeu **n**
      + Per a esborrar una línea sencera d'una vegada, fora del mode d'inserció de text, vos coloqueu en la línia y premeu **dd**
      + Per a guardar i eixir, eixiu del mode d'inserció de text (tecla **ESC**) i escriviu **:wq** (important els dos punts)

Després d'esborrar les pistes que el delaten, l'atacant decidix que utilitzar aquest usuari es perillós pel risc que té de que el pugen descobrir. Es per això que ha decidit fer servir un altre usuari. Consultant l'arxiu `/etc/passwd`ha vist que el mes indicat és un anomenat **altre_usuari**.

!!!task "Tasca 4 - Desxifrat de contrasenya"
    1. Treu la línia que et fa falta de l'arxiu `/etc/shadow`    
    2. En la teua màquina fes servir `johntheripper`per a desxifrar la contrasenya. Utilitza el diccionari que trobaràs en Aules.
    3. Comprova que, efectivament, pots conectar-te per SSH amb el nou usuari

Una vegada l'atacant ha fet login amb el nou usuari, descobrix un fitxer que l'interessa molt ubicat en el seu home. Per a exfiltrar eixa informació en eixe arxiu, l'atacant ha decidit aprofitar-se de que la màquina té instal·lada la utilitat ***rsync***.

!!!task "Tasca 5 - Exfiltració amb rsync"
    Fes servir *rsync* per a enviar l'arxiu **dades_interessants.txt** a la teua màquina amfitriona. Recorda que has de poder conectar-te per SSH a la teua màquina amfitrió.

## Administrador de sistemes

Després d'una àrdua tasca d'investigació, el administrador de sistemes ha descobert quina es la vulnerabilitat que ha fet servir l'atacant i ha de procedir a solucionar-la.


!!!task "Tasca 6 - Mitigació"
    Busca informació de com **<u>mitigar</u>** la vulnerabilitat i posa-lo en pràctica.


!!!warning "Atenció!"
    La tasca es considera correcta amb la mitigació. En cas de que vulgues fer-lo més real, pots fet l'actualització necessària però pot trigar molt de temps. Tens dos opcions, o deixar indicat el comandament o executar-lo i deixar-lo funcionar mentres continues amb l'examen.

L'administrador té un usuari propi:

!!!info
    + **usuari**: ubuntu
  
    + **contrasenya**: iessevero

Per a que no torne a pasar, l'administrador decideix establir una nova política de contrasenyes amb els següents requisits:

https://hostadvice.com/how-to/web-hosting/ubuntu/how-to-enable-and-enforce-secure-password-policies-on-ubuntu/

https://www.linuxtechi.com/lock-user-account-incorrect-login-attempts-linux/
