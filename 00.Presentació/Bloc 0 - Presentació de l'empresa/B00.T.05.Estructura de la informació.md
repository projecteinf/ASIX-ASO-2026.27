# Estructura carpetes

L'empresa disposarà d'una estructura de carpetes compartides al servidor. Aquesta estructura haurà de permetre separar: 

- els espais comuns de l'empresa, 
- els espais propis de cada departament, 
- les carpetes personals dels usuaris, 
- els projectes transversals 
- i les carpetes d'administració del sistema.

L'estructura inicial proposada és la següent:
```text
/empresa
├── comu
│   ├── intercanvi
│   ├── plantilles
│   ├── comunicats
│   └── interdepartamental
│
├── departaments
│   ├── direccio
│   │   ├── compartida
│   │   └── confidencial
│   │
│   ├── administracio
│   │   ├── compartida
│   │   ├── gestio_departament
│   │   └── documentacio_interna
│   │
│   ├── suport_tecnic
│   │   ├── compartida
│   │   ├── gestio_departament
│   │   ├── incidencies
│   │   └── scripts
│   │
│   └── produccio_musical
│       ├── compartida
│       ├── gestio_departament
│       ├── artistes
│       └── cataleg
│
├── usuaris
│   ├── usuari1
│   ├── usuari2
│   └── usuari3
│   └── ....
│
├── projectes
│   ├── campanya_estiu
│   └── migracio_servidors
│
└── administracio_sistema
    ├── backups
    ├── logs
    ├── configuracions
    └── inventari
```

## Carpeta `/empresa/departaments`

Conté les carpetes pròpies de cada departament.
Cada departament segueix una estructura semblant:
```text
/empresa/departaments/nom_departament
├── compartida
├── gestio_departament
└── carpetes_especifiques
```
- gestio_departament: carpeta amb accés limitat al cap de departament.
 
Per exemple:
```text
/empresa/departaments/administracio
├── compartida (tots els usuaris del departament d'administració)
├── gestio_departament (cap d'administració)
└── documentacio_interna (tots els usuaris del departament d'administració)
```
## Accessos

| Recurs                                                       | Direcció | Administració | Suport tècnic | Producció musical |     Informàtica | Externs |
| ------------------------------------------------------------ | -------: | ------------: | ------------: | ----------------: | --------------: | ------: |
| `/empresa/comu/intercanvi`                                   |      L/E |           L/E |           L/E |               L/E |         **L/E** |     L/E |
| `/empresa/comu/plantilles`                                   |      L/E |           L/E |             L |                 L |           **L** |      NA |
| `/empresa/comu/comunicats`                                   |      L/E |             L |             L |                 L |           **L** |      NA |
| `/empresa/comu/interdepartamental`                           |      L/E |            SP |            SP |                SP |          **SP** |      NA |
| `/empresa/departaments/direccio/compartida`                  |      L/E |            NA |            NA |                NA |          **NA** |      NA |
| `/empresa/departaments/direccio/gestio_departament`          |      L/E |            NA |            NA |                NA |          **NA** |      NA |
| `/empresa/departaments/direccio/confidencial`                |      L/E |            NA |            NA |                NA |          **NA** |      NA |
| `/empresa/departaments/administracio/compartida`             |        L |           L/E |            NA |                NA |          **NA** |      NA |
| `/empresa/departaments/administracio/gestio_departament`     |        L |        R: L/E |            NA |                NA |          **NA** |      NA |
| `/empresa/departaments/administracio/documentacio_interna`   |        L |           L/E |            NA |                NA |          **NA** |      NA |
| `/empresa/departaments/suport_tecnic/compartida`             |        L |            NA |           L/E |                NA |          **NA** |      NA |
| `/empresa/departaments/suport_tecnic/gestio_departament`     |        L |            NA |        R: L/E |                NA |          **NA** |      NA |
| `/empresa/departaments/suport_tecnic/incidencies`            |        L |            NA |           L/E |                NA |          **NA** |      NA |
| `/empresa/departaments/suport_tecnic/scripts`                |       NA |            NA |        R: L/E |                NA |          **NA** |      NA |
| `/empresa/departaments/produccio_musical/compartida`         |        L |            NA |            NA |               L/E |          **NA** |      NA |
| `/empresa/departaments/produccio_musical/gestio_departament` |        L |            NA |            NA |            R: L/E |          **NA** |      NA |
| `/empresa/departaments/produccio_musical/artistes`           |        L |            NA |            NA |               L/E |          **NA** |      NA |
| `/empresa/departaments/produccio_musical/cataleg`            |        L |            NA |           ATP |               L/E |          **NA** |      NA |
| `/empresa/departaments/informatica/compartida`               |        L |            NA |            NA |                NA |         **L/E** |      NA |
| `/empresa/departaments/informatica/gestio_departament`       |        L |            NA |            NA |                NA |      **R: L/E** |      NA |
| `/empresa/usuaris/usuariX`                                   |       NA |            NA |       **ATP** |                NA | **ADM tècnica** |      NA |
| `/empresa/projectes/campanya_estiu`                          |       NA |        **SP** |        **SP** |            **SP** |          **NA** |      NA |
| `/empresa/projectes/nou_cataleg`                             |       NA |            NA |        **SP** |            **SP** |          **NA** |      NA |
| `/empresa/projectes/migracio_servidors`                      |       NA |            NA |        **SP** |                NA |          **NA** |      NA |
| `/empresa/administracio_sistema/backups`                     |       NA |            NA |        **NA** |                NA |         **ADM** |      NA |
| `/empresa/administracio_sistema/logs`                        |       NA |            NA |       **ATP** |                NA |         **ADM** |      NA |
| `/empresa/administracio_sistema/configuracions`              |       NA |            NA |       **ATP** |                NA |         **ADM** |      NA |
| `/empresa/administracio_sistema/inventari`                   |       NA |            NA |         **L** |                NA |         **L/E** |      NA |


`/empresa/comu/intercanvi`, té per objectiu l'intercanvi temporal de documents amb usuaris externs
## Llegenda

| Valor      | Significat                                                                                             |
| ---------- | ------------------------------------------------------------------------------------------------------ |
| **NA**     | No pot accedir al recurs.                                                                              |
| **L**      | Pot consultar el contingut, però no modificar-lo.                                                      |
| **L/E**    | Pot llegir, crear, modificar i eliminar contingut.                                                     |
| **ADM**    | Pot gestionar el recurs, els permisos i el manteniment tècnic.                                         |
| **R: L/E** | Només el responsable del departament té lectura i escriptura; la resta del departament no hi accedeix. |
| **SP**     | Només hi accedeixen els usuaris assignats al projecte corresponent.                                    |
| **ATP**    | Accés temporal, justificat i registrat per resoldre una incidència.                                    |

