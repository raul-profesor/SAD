---
title: Elecció de SAI
description: En este ejercicio se simula un escenario real donde el alumna ha de elegir el SAI que mejor cubra los requerimientos de seguridad que son necesarios en la empresa
--- 

## Exercici guiat: Triant el SAI adequat per a sistemes crítics

### Objectiu
Els estudiants avaluaran els requisits d'alimentació i seleccionaran el SAI adequat per als sistemes crítics en un escenari. Se'ls proporcionarà consells per guiar-los a l'hora de triar els models de SAI correctes, calcular el temps d'execució i considerar mesures de redundància i ciberseguretat.

---

### Escenari
Sou l'administrador informàtic d'una empresa mitjana amb diversos sistemes crítics. A causa dels freqüents talls elèctrics, se vos ha encarregat d'escollir un sistema SAI per mantenir aquests sistemes operatius durant el temps necessari.

---

#### Sistemes crítics

| **Sistema**                | **Consum d'energía (Watts)** | **Nivell de prioritat** | 
|----------------------------|-------------------------------|--------------------|
| Servidor base de dades            | 800 W                         | High               | 
| Servidor Web                 | 600 W                         | High               | 
| Firewall                   | 100 W                         | Medium             | 
| Network Switch             | 80 W                          | Medium             | 
| Workstation (x5)           | 200 W cadascuna                   | Low            |   
| CCTV System (Cameras & NVR)| 400 W                         | Medium             | 
| Backup NAS                 | 300 W                         | Low                | 

---

!!!question "Tasca"
    El vostre objectiu és triar els models de SAI adequats que puguin gestionar el consum d'energia i assegurar-vos que cada sistema tingui el temps d'execució requerit. També hauríeu de considerar la redundància per als sistemes d'alta prioritat i abordar els problemes de ciberseguretat pel que fa a la gestió d'SAI.

--- 

### Passos i consells

#### Pas 1:  Calculeu el consum total d'energia del sistema

!!!tip "Pista"
        El consum total d'energia és la suma de la potència absorbida de tots els sistemes. Assegureu-vos d'incloure tots els sistemes al vostre càlcul. El consum d'energia es dóna en watts.

---

#### Pas 2: Converteix el consum d'energia a la capacitat del SAI (VA) per a tot el sistema

!!!tip "Pista"
        Els sistemes SAI solen estar classificats en Volt-Amps (VA). Per convertir la potència total en watts a VA, utilitzeu la fórmula següent:

        $$ 
        \text{Capacitat del SAI (VA)} = \frac{\text{Potència total (watts)}}{\text{Factor de potència}} 
        $$

        On el factor de potència és generalment de 0,8 per a la majoria de les unitats SAI. Aquesta conversió és necessària perquè els sistemes SAI tenen en compte la potència reactiva, per això VA i watts difereixen.

!!!question "Tasca"
    Busca, troba i indica un SAI adequat que puga cobrir tota la potència del sistema.
----

#### Pas 3: Calculeu el temps d'execució del SAI per a tot el sistema

!!!tip "Pista"
    La majoria de fulls de dades del SAI proporcionen corbes o taules de temps d'execució que mostren quant de temps el SAI pot suportar una càrrega específica. Si coneixeu la càrrega de potència en watts i la capacitat del SAI, utilitzeu aquests recursos per determinar quant de temps el SAI proporcionarà energia de reserva.

    També podeu utilitzar la fórmula simplificada per aproximar el temps d'execució:
    $$
    \text{Temps d'execució del SAI (minuts)} = \frac{\text{Capacitat del SAI (Wh)}}{\text{Càrrega del sistema (Watts)}}
    $$

---

#### Pas 4: Dividiu els sistemes per prioritat

No tots els sistemes necessiten el mateix temps de funcionament. Agrupeu els sistemes per nivell de prioritat per assignar millor els recursos del SAI. Els sistemes crítics com el servidor de bases de dades i el servidor web haurien de tenir temps d'execució més llargs i possiblement redundància, mentre que els sistemes de prioritat més baixa poden tenir temps d'execució més curts.

+ **Sistemes d'alta prioritat (servidor de bases de dades, servidor web):** necessiten entre 20 i 40 minuts de temps d'activitat.

+ **Sistemes de prioritat mitjana (tallafoc, commutador de xarxa, CCTV):** necessiten entre 20 minuts i 30 minuts de funcionament.

+ **Sistemes de baixa prioritat (estacions de treball, NAS de còpia de seguretat):** només necessiten 8 minuts per a un apagat segur.

---
  
#### Pas 5: Seleccioneu els models de SAI adequats
Utilitzeu la taula següent per ajudar-vos a triar el SAI adequat per a cada grup de sistemes en funció dels seus requisits d'alimentació i necessitats de temps d'execució.
Penseu si necessiteu comprar diverses unitats SAI o una de més gran per cobrir tots els sistemes.

!!!tip "Pista"
    Busqueu les especificacions de cadascún dels SAI i consulteu les gràfiques de *runtime* per tal de completar la taula

| **Model SAI**        | **Capacitat (VA)** | **Factor potència** | **Càrrega màxima (Watts)** | **Temps d'execució en càrrega màxima (Minuts)** | **Temps d'execució amb 50% de càrrega (Minuts)** | **Preu (€)** |
|----------------------|-------------------|------------------|----------------------|------------------------------------|-----------------------------------|-----------|
| APC SAI Smart UPS SRT 1500VA (SRT1500XLA)  | 1500              | 0.9              |                 |                                  |                                |     800€  |
| Eaton 5P 2200VA (9PX2200GRT-L)      | 2200              | 0.9091              |                 |                                |                               |    1715€  |
| CyberPower 3000VA  (OL3000RTXL2U)    | 3000              | 0.9              |                 |                               |                                |  2600€  |
| CyberPower 5000VA  (PR5000LCDRTXL5U)    | 5000              | 0.9              |                 |                               |                                |  3800€  |

---

#### Pas 6: Considereu la redundància i la ciberseguretat

!!!tip "Pista"
    Per als sistemes d'alta prioritat (p. ex., servidor de bases de dades, servidor web), considereu la possibilitat d'implementar la redundància utilitzant dues unitats SAI si fera falta. La redundància garanteix que si falla un SAI, la segona unitat pot fer-se càrrec, mantenint el sistema operatiu.

    A més, assegureu-vos que el SAI admet la supervisió remota (mitjançant SNMP o interfícies basades en web) perquè pugueu rebre alertes i controlar l'estat de la bateria. 

### Preguntes per respondre al vostre informe:

1. Consum total d'energia: quin és el consum total d'energia de tots els sistemes?
    
    !!!tip "Pista" 
        Suma la potència (en watts) de tots els sistemes.

2. Capacitat del SAI: Quina és la capacitat total del SAI (en VA) necessària per a tots els sistemes?

    !!!tip "Consell" 
        Utilitzeu la fórmula que se vos indica i un factor de potència de 0,8 per convertir watts a VA.

3. Selecció de SAI: quins models de SAI heu triat i per què?

    !!!tip "Consell"
        Tingueu en compte el temps d'execució, la càrrega i el preu quan seleccioneu el SAI. Procureu economitzar al màxim la vostra elecció.

4. Redundància: heu inclòs alguna redundància per a sistemes d'alta prioritat? Per què o per què no?

    !!!tip "Suggeriment" 
        La redundància pot evitar temps d'inactivitat en cas d'avaria del SAI.

5. Consideracions de ciberseguretat: quines mesures de seguretat prendràs per garantir que la interfície de gestió de l'SAI estigui segura?

    !!!tip "Pista"
        Si tenim una eina de monitorització del SAI a la que s'accedix mitjantçant un accés web, què faríes per a tindre un accés segur?


### Entrega final:
Un informe que inclou:

+ Càlculs de potència i temps d'execució.
+ Selecció i justificació del model de SAI.
+ Planificació de redundància per a sistemes d'alta prioritat.
+ Mesures de ciberseguretat per assegurar la gestió de SAI.
+ Cost total de la implementació amb tots els SAI.