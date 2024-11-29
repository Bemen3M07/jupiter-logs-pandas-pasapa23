[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/ULiw8LbN)
# Empty
Repositori buit

Exercici 1: 
Explica quines comandes de Linux Pots fer servir a l’hora d’analitzar logs escrits a fitxer per a:
- Veure contínuament els logs que es van escrivint a un arxiu
Per a veure en els ultims logs (-f) que s'han escrit: 
tail -f nom_del_fitxer.log
I si vols veure un nombre de logs en concret (-n nombre_de_logs): 
tail -n 10 -f nom_del_fitxer.log
- Cercar una paraula concreta dintre d’un arxiu de log
grep "paraula_a_cercar" nom_del_fitxer.log

Exercici 2:
2. Que creieu que és millor mostrar els logs per exemple a la terminal durant l'execució del programa o bolcar-los en un fitxer de text?
- Si el teu objectiu és depurar o monitoritzar un programa mentre s'està desenvolupant, mostrar els logs a la terminal és més pràctic.
- Si el teu objectiu és guardar els detalls per a un anàlisi posterior, en entorns de producció o per a un seguiment a llarg termini, bolcar els logs en un fitxer és la millor opció.
En entorns de producció, sempre és més útil tenir els logs en fitxers per a la seva supervisió, anàlisi i diagnòstic posterior.

3. Omple la següent taula amb expmple, avantantges, i desavantatges de les següents maneres de fer logs:
- Fent servir la configuració per defecgte del mòdul logging:
  Exemple:
  python import logging
  logging.basicConfig(level=logging.INFO)
  logging.info("Missatge de log")
  
  Avantatges:
- Molt fàcil d'utilitzar: Configuració mínima, ideal per a aplicacions senzilles o prototips.
- Configurable ràpidament: Només cal definir el nivell de log i el format, sense necessitat de gestionar molts handlers.

  Desavantatges:
- Limitat en flexibilitat: No permet configurar múltiples handlers de manera fàcil (per exemple, enviar logs a la consola i a un fitxer alhora).
- No és adequat per a aplicacions grans: Si el projecte creix, es fa difícil gestionar els logs de manera efectiva.
  
- Instanciant un objecte logger i parametritzantlo des de programa:
  Exemple:
  python import logging logger = logging.getLogger('exemple')
  logger.setLevel(logging.INFO)
  logger.info("Missatge de log")
  
  Avantatges:
  - Més control sobre la configuració: Pots afegir múltiples handlers (per exemple, fitxer, consola) i personalitzar la configuració de cada handler (nivells de log, formats, etc.).
  - Flexible i ampliable: Permet crear múltiples loggers amb configuracions específiques per a diferents parts de l'aplicació.
    
  Desavantatges:
  - Més complexitat inicial: S’ha d’especificar tot manualment, incloent la configuració dels handlers i el format. Això pot ser complicat per a aplicacions petites o per a  deesenvolupadors poc experimentats.
  - Manteniment manual: Cada canvi en la configuració de logging requereix modificar el codi, el que pot ser menys pràctic en projectes grans o en entorns de producció.


- instanciant un objecte logger a partir d’una configuració emmagatzemada a fitxer:
  Exemple:
  python import logging from logging.config
  import fileConfig
  fileConfig('logging.conf') logger = logging.getLogger('exemple')
  logger.info("Missatge de log")
  
  Avantatges:
  - Separació de la configuració del codi: La configuració es guarda en un fitxer extern, fet que permet modificar els logs sense tocar el codi font. Ideal per a entorns de   producció.
  - Facilita la gestió centralitzada de la configuració de logging: Pots tenir un fitxer de configuració comú per a tota l'aplicació, facilitant el manteniment i la consistència  entre entorns (desenvolupament, producció, etc.).
  - Molt flexible: Permet definir diversos loggers, handlers i formats en el mateix fitxer.
  
  Desavantatges:
  - Dependència d’un fitxer extern: Si el fitxer de configuració no està ben gestionat o no es troba disponible, pot fallar la configuració dels logs.
  - Menys directe i pot ser difícil per a petits projectes: La necessitat de tenir un fitxer de configuració extern pot ser excessiva per a aplicacions senzilles, on una configuració directa al codi és més ràpida i eficient.
  - Pot requerir una càrrega addicional per llegir el fitxer: El sistema ha de carregar el fitxer de configuració, fet que afegeix complexitat i pot ser menys eficient que una configuració directa.

4. Cerca llibreries de logs en altres llenguatjes (al menys 2, i identifica cóm resolen les següents característiques típiques d’un sistema de logging.
Llenguatge: C#
Nom de la llibreria: log4net
És nativa del llenguatge?: Sí
URL per descargar-se la llibreria: https://logging.apache.org/log4net/ 
Inicialització de l’objecte de logger: log4net.Config.XmlConfigurator.Configure()
Nivells de log disponibles: Trace, Debug, Info, Warn, Error, Fatal
Mètode per fer log: log.Info("message")
Tipus de manegadors: Pantalla, fitxer, JSON (configuració personalitzada)
Opcions de format: JSON, coloritzat, personalitzat

Llenguatge: Java
Nom de la llibreria: Log4j 2
És nativa del llenguatge?: No
URL per descarregar-se la llibreria: https://logging.apache.org/log4j/2.x/
Inicialització de l’objecte de logger: Logger logger = LogManager.getLogger(Example.class);
Nivells de log disponibles: TRACE, DEBUG, INFO, WARN, ERROR, FATAL
Mètode per fer log: logger.info("Missatge d'informació");
Tipus de manegadors: Consola, fitxer, bases de dades, servidor de missatges

Exercici 3:
Funcionalitat de cada una de les eines presentades.
Pandas:
Pandas és una llibreria de Python molt utilitzada per a la manipulació i anàlisi de dades. Està dissenyada per treballar amb estructures de dades tabulars, com taules, i facilita tasques com:

- Maneig de dades tabulars: Permet treballar amb estructures com DataFrames i Series, que permeten emmagatzemar i manipular dades de manera eficient.
- Neteja de dades: Proporciona eines poderoses per tractar valors nuls, duplicats, tipus de dades i altres aspectes que poden afectar la qualitat de les dades.
- Operacions d'agrupament, fusionar, i unir dades: Permet realitzar operacions d'agrupament, ordenació, fusió de taules i molt més.
- Visualització: Integració amb altres llibreries com Matplotlib i Seaborn per a la visualització gràfica de dades.
En resum, Pandas és ideal per a l'anàlisi i manipulació de dades en formats com CSV, Excel, SQL, entre d'altres.

Jupyter Notebook:
Jupyter Notebook és una aplicació interactiva de codi obert que permet escriure i executar codi Python en blocs de cel·les dins d'un mateix document, anomenat "notebook". Les seves funcionalitats principals inclouen:

- Executar codi de manera interactiva: Permet executar el codi en blocs i veure els resultats de manera immediata, facilitant la depuració i exploració de dades.
- Documentació combinada amb codi: Pots combinar codi amb text explicatiu (en format Markdown) i altres elements multimèdia com gràfics, taules i imatges, fent-lo una eina poderosa per a la presentació de projectes.
- Suport per múltiples llenguatges: Tot i que originalment dissenyat per Python, Jupyter també pot executar codi en altres llenguatges com R, Julia i Scala mitjançant el sistema de kernels.
- Ideal per a la docència i la investigació: Permet crear tutorials i documents interactius per ensenyar i presentar els resultats de manera clara i visual.

ReportLab:
ReportLab és una llibreria Python dissenyada per generar documents PDF dinàmics i personalitzats. Les seves funcionalitats principals inclouen:

- Generació de PDFs: Permet crear documents PDF des de zero mitjançant codi, afegint text, imatges, taules i gràfics.
- Personalització de dissenys: Permet definir dissenys complets per als documents, incloent marges, fonts, estils i més, de manera flexible i potent.
- Suport per gràfics: ReportLab també permet generar gràfics vectorials, perfectes per a informes i documents amb visualitzacions de dades.
- Automatització de la creació de PDFs: Ideal per crear informes automatitzats, factures, documents legals o qualsevol tipus de contingut en PDF de manera programàtica.
ReportLab és molt utilitzat en la creació d'informes empresarials, facturació automàtica i generació de documents personalitzats a gran escala.


