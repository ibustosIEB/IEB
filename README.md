EAS CC — Registre d'Evidències de Capacitats Clau
Aplicació web per a l'avaluació per indicadors de les Capacitats Clau (CC) en cicles formatius de grau superior (CFGS). Construïda amb Google Apps Script + Google Sheets.
Estructura del projecte
eas-cc/

├── Code.gs       # Backend: router, lògica de negoci, lectura/escriptura de Sheets

├── Index.html    # Frontend: SPA (HTML + CSS + JS inline)

└── README.md
Arquitectura
Full PRINCIPAL (Google Sheets)
Pestanya
Contingut
Usuaris
Llista d'usuaris amb rol, classe, mòduls assignats i contrasenya
Mòduls
Catàleg de mòduls amb codi, nom, curs i ID del Sheet de mòdul
Activitats -> Indicadors
Mapeig d'activitats a codis d'indicador (catàleg global)
Indicadors
Definició de cada indicador: capacitat, text, colors

Sheets de MÒDUL (un per mòdul)
Pestanya
Contingut
Organització Mòdul
Projectes del mòdul: professors, número, nom
Activitats Mòdul
Activitats pròpies del mòdul (no del catàleg global)
A / B / C
Blocs de notes per grup-classe, organitzats per projecte i indicador
Resum A / Resum B / Resum C
Resum calculat automàticament per capacitat i projecte

Rols d'usuari
admin — accés total
professor — accés als mòduls i projectes assignats
alumne — (reservat per a fases posteriors)
Capacitats Clau avaluades
ID
Nom
c1
Organització del treball
c2
Iniciativa
c3
Responsabilitat en el treball
c4
Autonomia
c5
Treball en equip
c6
Relacions interpersonals
c7
Resolució de problemes

Escala de valoració
Valor
Color
Nivell
1
🔴 #E25563
No assolit
4
🟠 #E0A23C
En procés
7
🔵 #4F8EF7
Assolit
10
🟢 #3FB27F
Excel·lència
NA
⬜ #D9D9D9
No avaluable

Desplegament
Obre script.google.com i crea un nou projecte.
Copia el contingut de Code.gs al fitxer Code.gs del projecte.
Crea un fitxer HTML anomenat Index i copia el contingut de Index.html.
Publica com a Aplicació web (Desplegar > Nova implementació > Aplicació web).
Executa createModuleSheets() manualment una vegada per crear els Sheets de cada mòdul.
Funcions principals del backend
Funció
Descripció
handleRequest(action, payload)
Router únic per a totes les peticions del frontend
createModuleSheets()
Crea/repara els Sheets de cada mòdul (idempotent)
saveRegistre_(p)
Desa un bloc d'avaluació en la pestanya de classe corresponent
rebuildResum_(ss, letter)
Recalcula i escriu la pestanya Resum X del mòdul
debugV4()
Funció de depuració: comprova ping i login des del Logger

Accions de l'API (via handleRequest)
ping · login · getCourses · getModules · getClasses

getProjects · getActivityTypes · getActivityIndicators

getCapabilities · saveActivity · getStudents

saveRegistre · getEvidencies · getBlockDetail

deleteRegistre · getModuleResum · getInici

listProjects · saveProject · deleteProject · getAllProfs

