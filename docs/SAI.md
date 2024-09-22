---
title: Elecció de SAI
description: En este ejercicio se simula un escenario real donde el alumna ha de elegir el SAI que mejor cubra los requerimientos de seguridad que son necesarios en la empresa
--- 

## Exercici guiat: Triant el SAI adequat per a sistemes crítics

### Objectiu
Els estudiants avaluaran els requisits d'alimentació i seleccionaran el SAI adequat per als sistemes crítics en un escenari. Se'ls proporcionarà consells per guiar-los a l'hora de triar els models de SAI correctes, calcular el temps d'execució i considerar mesures de redundància i ciberseguretat.

---

### Escenari
Sou l'administrador informàtic d'una empresa mitjana amb diversos sistemes crítics. A causa dels freqüents talls elèctrics, se us ha encarregat d'escollir un sistema SAI per mantenir aquests sistemes operatius durant el temps necessari.

---

#### Sistemes crítics

| **Sistema**                | **Consum d'energía (Watts)** | **Nivell de prioritat** | **Uptime (temps de funcionament) requerit** |
|----------------------------|-------------------------------|--------------------|---------------------|
| Database Server            | 800 W                         | High               | 30 minuts          |
| Web Server                 | 600 W                         | High               | 15 minuts          |
| Firewall                   | 100 W                         | Medium             | 15 minuts          |
| Network Switch             | 80 W                          | Medium             | 15 minuts          |
| Workstation (x5)           | 200 W cadascú                    | Low                | 10 minuts          |
| CCTV System (Cameras & NVR)| 400 W                         | Medium             | 1 hora             |
| Backup NAS                 | 300 W                         | Low                | 10 minuts          |

---

!!!question "Tasca"
    El vostre objectiu és triar els models de SAI adequats que puguin gestionar el consum d'energia i assegurar-vos que cada sistema tingui el temps d'execució requerit. També hauríeu de considerar la redundància per als sistemes d'alta prioritat i abordar els problemes de ciberseguretat pel que fa a la gestió d'UPS.

--- 

### Passos i consells


1. calculeu el consum total d'energia

    !!!tip "Pista"
         El consum total d'energia és la suma de la potència absorbida de tots els sistemes. Assegureu-vos d'incloure tots els sistemes al vostre càlcul. El consum d'energia es dóna en watts.

2. Converteix el consum d'energia a la capacitat del SAI (VA)
   
    !!!tip "Pista"
            Els sistemes UPS solen estar classificats en Volt-Amps (VA). Per convertir la potència total en watts a VA, utilitzeu la fórmula següent:

            $$ 
            \text{Capacitat del SAI (VA)} = \frac{\text{Potència total (watts)}}{\text{Factor de potència}} 
            $$

            On el factor de potència és generalment de 0,8 per a la majoria de les unitats SAI. Aquesta conversió és necessària perquè els sistemes SAI tenen en compte la potència reactiva, per això VA i watts difereixen.

            Per exemple, si calculeu que la potència total és de 3280 W, el requisit de VA seria:

            $$
            \text{Capacitat del SAI (VA)} = \frac{3280}{0,8} = 4100  \text{VA} 
            $$



On el factor de potència és generalment de 0,8 per a la majoria de les unitats SAI. Aquesta conversió és necessària perquè els sistemes SAI tenen en compte la potència reactiva, per això VA i watts difereixen.

Per exemple, si calculeu que la potència total és de 3280 W, el requisit de VA seria:

[ \text{Capacitat del SAI (VA)} = \frac{3280}{0,8} = 4100 , \text{VA} ]
1. Calculeu el temps d'execució de l'UPS per a cada sistema
2. Dividiu els sistemes per prioritat
3. Seleccioneu els models de SAI adequats

| **UPS Model**        | **Capacity (VA)** | **Power Factor** | **Max Load (Watts)** | **Runtime at Full Load (Minutes)** | **Runtime at 50% Load (Minutes)** | **Price** |
|----------------------|-------------------|------------------|----------------------|------------------------------------|-----------------------------------|-----------|
| APC Smart-UPS 1500VA  | 1500              | 0.8              | 1200                 | 4                                  | 14                                | $500      |
| Eaton 5P 2200VA       | 2200              | 0.9              | 1980                 | 7                                  | 18                                | $900      |
| CyberPower 3000VA     | 3000              | 0.8              | 2400                 | 9                                  | 27                                | $1,200    |

1. Considereu la redundància i la ciberseguretat


Sens dubte! A continuació es mostra un exercici similar, però aquesta vegada amb consells per guiar els estudiants sobre com prendre decisions sobre la selecció del SAI, el consum d'energia i les consideracions de ciberseguretat.

Exercici guiat: escollir el SAI adequat per a sistemes crítics
Objectiu:
Els estudiants avaluaran els requisits d'alimentació i seleccionaran el SAI adequat per als sistemes crítics en un escenari. Se'ls proporcionarà consells per guiar-los a l'hora de triar els models de SAI correctes, calcular el temps d'execució i considerar mesures de redundància i ciberseguretat.

Escenari:
Sou l'administrador informàtic d'una empresa mitjana amb diversos sistemes crítics. A causa dels freqüents talls elèctrics, se us ha encarregat d'escollir un sistema SAI per mantenir aquests sistemes operatius durant el temps necessari.

Sistemes crítics:
Consum d'energia del sistema (Watts) Nivell de prioritat Temps de funcionament necessari
Servidor de bases de dades 800 W Alt 30 minuts
Servidor web 600 W Alt 15 minuts
Tallafoc 100 W Mitjà 15 minuts
Commutador de xarxa 80 W Mitjà 15 minuts
Estació de treball (x5) 200 W cadascuna Baixa 10 minuts
Sistema CCTV (Càmeres i NVR) 400 W Mitjà 1 hora
Còpia de seguretat NAS 300 W Baixa 10 minuts
Tasca:
El vostre objectiu és triar els models de SAI adequats que puguin gestionar el consum d'energia i assegurar-vos que cada sistema tingui el temps d'execució requerit. També hauríeu de considerar la redundància per als sistemes d'alta prioritat i abordar els problemes de ciberseguretat pel que fa a la gestió d'UPS.

Passos i consells:
Pas 1: calculeu el consum total d'energia
Pista:
El consum total d'energia és la suma de la potència absorbida de tots els sistemes. Assegureu-vos d'incloure tots els sistemes al vostre càlcul. El consum d'energia es dóna en watts.

[ \text{Consum total d'energia (watts)} = 800 , (\text{Servidor DB}) + 600 , (\text{Servidor web}) + \dots ]

Pas 2: Converteix el consum d'energia a la capacitat del SAI (VA)
Pista:
Els sistemes UPS solen estar classificats en Volt-Amps (VA). Per convertir la potència total en watts a VA, utilitzeu la fórmula següent:

[ \text{Capacitat del SAI (VA)} = \frac{\text{Potència total (watts)}}{\text{Factor de potència}} ]

On el factor de potència és generalment de 0,8 per a la majoria de les unitats SAI. Aquesta conversió és necessària perquè els sistemes SAI tenen en compte la potència reactiva, per això VA i watts difereixen.

Per exemple, si calculeu que la potència total és de 3280 W, el requisit de VA seria:

[ \text{Capacitat del SAI (VA)} = \frac{3280}{0,8} = 4100 , \text{VA} ]

Pas 3: calculeu el temps d'execució de l'UPS per a cada sistema
Pista:
La majoria de fulls de dades del SAI proporcionen corbes o taules de temps d'execució que mostren quant de temps el SAI pot suportar una càrrega específica. Si coneixeu la càrrega de potència en watts i la capacitat del SAI, utilitzeu aquests recursos per determinar quant de temps el SAI proporcionarà energia de reserva.

Per exemple, si un SAI pot gestionar una càrrega de 2400 W i el temps d'execució a plena càrrega és de 9 minuts, i el vostre sistema només utilitza 1200 W (50% de la capacitat), el temps d'execució serà més llarg, uns 27 minuts segons les dades. .

També podeu utilitzar la fórmula simplificada per aproximar el temps d'execució:

[ \text{Temps d'execució del SAI (minuts)} = \frac{\text{Capacitat del SAI (Wh)}}{\text{Càrrega del sistema (Watts)}} ]

Pas 4: Dividiu els sistemes per prioritat
Pista:
No tots els sistemes necessiten el mateix temps de funcionament. Agrupeu els sistemes per nivell de prioritat per assignar millor els recursos del SAI. Els sistemes crítics com el servidor de bases de dades i el servidor web haurien de tenir temps d'execució més llargs i possiblement redundància, mentre que els sistemes de prioritat més baixa poden tenir temps d'execució més curts.

Sistemes d'alta prioritat (servidor de bases de dades, servidor web): necessiten entre 15 i 30 minuts de temps d'activitat.
Sistemes de prioritat mitjana (tallafoc, commutador de xarxa, CCTV): necessiten entre 15 minuts i 1 hora de funcionament.
Sistemes de baixa prioritat (estacions de treball, NAS de còpia de seguretat): només necessiten 10 minuts per a un apagat segur.
Pas 5: seleccioneu els models de SAI adequats
Pista:
Utilitzeu la taula següent per ajudar-vos a triar el SAI adequat per a cada grup de sistemes en funció dels seus requisits d'alimentació i necessitats de temps d'execució. Penseu si necessiteu comprar diverses unitats SAI o una de més gran per cobrir tots els sistemes.

Model de SAI Capacitat (VA) Factor de potència Càrrega màxima (Watts) Temps d'execució a càrrega completa (minuts) Temps de funcionament al 50% de càrrega (minuts) Preu
APC Smart-UPS 1500VA 1500 0,8 1200 4 14 500 $
Eaton 5P 2200VA 2200 0,9 1980 7 18 900 $
CyberPower 3000VA 3000 0,8 2400 9 27 1.200 $
Pista 1: Comenceu per comprovar si un sol SAI pot gestionar tota la càrrega d'energia. Per exemple, si la potència total és de 3280 W, caldria un SAI de 4100 VA.
Pista 2: si cap SAI pot proporcionar el temps d'execució necessari per a tots els sistemes, dividiu la càrrega en diversos sistemes SAI, agrupant-los per nivell de prioritat.
Pista 3: mireu les corbes de temps d'execució a les fulles de dades per comprovar quant de temps cada SAI suportarà els sistemes amb càrregues totals i parcials.
Pas 6: considereu la redundància i la ciberseguretat
Pista:
Per als sistemes d'alta prioritat (p. ex., servidor de bases de dades, servidor web), considereu la possibilitat d'implementar la redundància utilitzant dues unitats SAI. La redundància garanteix que si falla un SAI, la segona unitat pot fer-se càrrec, mantenint el sistema operatiu.

A més, assegureu-vos que el SAI admet la supervisió remota (mitjançant SNMP o interfícies basades en web) perquè pugueu rebre alertes i controlar l'estat de la bateria. Assegureu-vos que aquestes funcions de gestió estiguin protegides, inclosos nosaltres utilitzar contrasenyes segures, desactivar serveis innecessaris i xifrar la comunicació entre el SAI i els sistemes de monitorització.

Preguntes per respondre al vostre informe:
Consum total d'energia: quin és el consum total d'energia de tots els sistemes?

Pista: suma la potència (en watts) de tots els sistemes.
Capacitat del SAI: Quina és la capacitat total del SAI (en VA) necessària per a tots els sistemes?

Consell: utilitzeu la fórmula i un factor de potència de 0,8 per convertir watts a VA.
Selecció de SAI: quins models de SAI vau triar i per què?

Consell: tingueu en compte el temps d'execució, la càrrega i el preu quan seleccioneu el SAI.
Redundància: heu inclòs alguna redundància per a sistemes d'alta prioritat? Per què o per què no?

Suggeriment: la redundància pot evitar temps d'inactivitat en cas d'avaria del SAI.
Consideracions de ciberseguretat: quines mesures de seguretat prendràs per garantir que la interfície de gestió de l'UPS estigui segura?

Esquema de la solució:
A continuació s'explica com s'aproximarà a la solució en funció dels passos i consells proporcionats:

Consum total d'energia:

Sumeu el consum d'energia de tots els sistemes: [ 800 + 600 + 100 + 80 + 1000 + 400 + 300 = 3280 , \text{W} ]
Convertir a VA:

Utilitzant un factor de potència de 0,8: [ \text{Capacitat del SAI (VA)} = \frac{3280}{0,8} = 4100 , \text{VA} ]
Seleccioneu els models de SAI:

Necessites un total de 4100 VA per donar suport a tots els sistemes.
Per als sistemes d'alta prioritat (1400 W), utilitzeu dues unitats CyberPower 3000VA per garantir 30 minuts de temps d'activitat amb redundància.
Per als sistemes de prioritat mitjana (580 W), utilitzeu una unitat Eaton 5P 2200VA, que proporciona més d'1 hora de temps d'execució amb una càrrega del 30%.
Per als sistemes de baixa prioritat (1300 W), dues unitats APC Smart-UPS 1500VA manejaran la càrrega i proporcionaran uns 10-15 minuts de temps d'execució.
Redundància:

La redundància es proporciona per als sistemes d'alta prioritat mitjançant l'ús de dues unitats UPS CyberPower 3000VA. Si un falla, l'altre pot continuar donant suport als sistemes.
Consideracions de ciberseguretat:

Assegureu-vos que la supervisió remota estigui habilitat per al SAI, assegureu les interfícies de gestió amb contrasenyes fortes i restringiu l'accés a la xarxa al SAI.
Utilitzeu l'encriptació per a les comunicacions (p. ex., SNMPv3 o HTTPS) entre el SAI i el programari de supervisió.
Entrega final:
Un informe que inclou: 1.