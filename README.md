## Harmonium
### Concepte de l'Aplicació
Harmonium és una aplicació web d'intel·ligència musical per a DJs que transforma les seves llibreries caòtiques d'iTunes, Traktor o un directori en una única base de dades, enriquida i perfectament organitzada, tot de manera local, privada i segura al navegador de l'usuari.

### El Problema que Resol
El DJ digital s'enfronta a una sèrie de problemes que consumeixen molt de temps:
 * Metadades inconsistents: Gèneres, anys i altres etiquetes incorrectes o incompletes.
 * Anàlisi Manual: La necessitat d'escoltar i comptar manualment l'estructura de les cançons (frases, parts de la cançó) per a una mescla precisa.
 * Dades Fragmentades: La informació útil està dispersa entre diferents programes (iTunes, Traktor, Discogs, Spotify) i no es pot combinar.
 * Manca d'Informació Clau: Les llibreries convencionals no ofereixen dades acústiques com el nivell d'energia, la "ballabilitat", la tonalitat musical o l'espectre acustic.
La Solució que Aporta
Harmonium actua com un assaistent intel·ligent que:
 * Centralitza: Fusiona les llibreries en una única base de dades local.
 * Enriqueix: Utilitza APIs externes per afegir automàticament dades professionals (any, segell, estils, energia, etc.), i les organitza tant a les metadates del fitxer local com a la pròpia col·lecció utilitzant camps genèrics com "comments".
 * Analitza: Aplica anàlisi estructural per entendre la composició de les cançons, identificant i comptant les seves parts clau.
 * Facilita: Ofereix eines per organitzar la llibreria i preparar sessions de manera eficient.
   
## 2. Flux d'Interacció
 *Es mostra l'accés d'usuari i registre com a uniques opcions disponibles.
 * Importació Inicial i establiment del directori: L'usuari obre Harmonium i se li presenta el component de configuració per carregar els seus arxius de llibreria. Selecciona els seus fitxers Library.xml (iTunes) i collection.nml (Traktor), si escau, o el directori musical.
 * Processament Automàtic: Una barra de progrés informa l'usuari mentre Harmonium parseja, fusiona les dades de les dues fonts i les desa a la base de dades local del navegador. Aquest procés només es fa la primera vegada i es mostren tips de workflow mentre dura la tasca.
 * Vista Principal de la Llibreria: En les visites següents, l'aplicació carrega instantàniament la llibreria des de la base de dades local. L'usuari veu una taula potent i fluida (amb virtual scrolling) amb tota la seva música unificada, on pot veure dades de Traktor (com la tonalitat) al costat de dades d'iTunes.
 * Enriquiment Intel·ligent: L'usuari selecciona un grup de cançons i fa clic a "Enriquir". Harmonium consulta les APIs externes i omple automàticament les columnes buides amb l'any correcte, el segell discogràfic (de Discogs), l'energia, la ballabilitat (de Spotify) i l'anàlisi estructural (de Spotify).
 * Organització i Acció: El DJ utilitza els filtres avançats per preparar la seva sessió (ex: "Mostra'm cançons de 'Hard Trance' amb una pujada de 16 compassos i tonalitat 8m"). Selecciona els resultats i fa clic a "Exportar a .m3u" per tenir una playlist a punt per a realitzar la sessió en directe.
   
## 3. Disseny Visual
 * La vista principal amb la barra superior amb el cercador i el menú d'usuari
 * Aside lateral esquerre de llistes i filtres guardats (collapse en movil)
 * Router-outlet amb la taula de cançons amb filtres globals; el contingut per a manejar l'experiència d'usuari; i la configuració del reproductor i clo·lecció.
 * El panell de detalls tècnics, reproductor i espectograma que apareix en seleccionar una cançó, que serà flotant en sortir aquesta de l'scroll (o bé fixed a movil).

## 4. Tecnologies

 * Framework: Angular
 * Llenguatge: TypeScript
 * Base de Dades: IndexedDB + Dexie.js per a un emmagatzematge local i privat.
 * Interfície d'Usuari:
   * Angular Material (Navegació)
   * Wavesurfer.js (per a la visualització de l'espectogram musical i la seva interacció, inclou compatibilitat amb .flac per a ios i safari) + Web Audio API (Filtres de banda) 
 * APIs de Dades:
   * Discogs API (per a dades de publicació com l'any, el segell i els estils).
   * Spotify API (per a l'anàlisi acústica i estructural de la música）.
   * cyanite.ai (per a un analisi més extens com a qualitat premium). 
 * Interacció amb Fitxers Locals: File System Access API (per a llegir les carpetes de música).
 * js-id3-writer (per incrustar les metadates als fitxers locals i fer-los perdurables fora de la biblioteca)
 * Qualitat de Codi: ESLint i Prettier (per a garantir un codi net, consistent i lliure d'errors).
 * Progressive Web App amb Media Session API + Service worker
