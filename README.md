# Viatge-Pràctica


## Pràctica P5.1: organitza un viatge amb Google

Jaden Cuevas Medina
**Mòdul:** 0228 · Aplicacions web · RA5
**Viatge:** República Dominicana, 7 dies (15–21 de març de 2027), pressupost màxim 1.500 €

---

## Fase 1: el correu

### 1. Sis eines de Google


| Eina | Propòsit | Target (públic) |
|---|---|---|
| Gmail | Enviar, rebre i organitzar correu electrònic | Qualsevol usuari, estudiants i professionals |
| Google Calendar | Gestionar agenda, esdeveniments i recordatoris | Estudiants, professionals i equips |
| Google Maps | Cercar llocs i dibuixar rutes | Viatgers i conductors |
| Google Sheets | Fulls de càlcul amb fórmules i pressupostos | Estudiants, administratius i empreses |
| Google Drive | Guardar i compartir fitxers al núvol | Qualsevol usuari i equips |
| Google Docs | Documents de text col·laboratius | Estudiants, professionals i equips |

### Diferència entre IMAP i POP3

POP3 descarrega els missatges al teu ordinador i normalment els esborra del servidor, de manera que només els pots llegir des d'aquell aparell.
IMAP, en canvi, deixa els missatges al servidor i els mostra des de qualsevol dispositiu connectat.
Per això, amb IMAP el mateix correu es veu igual a l'ordinador, al mòbil i a la tauleta.
A més, IMAP sincronitza carpetes, etiquetes i missatges llegits, cosa que POP3 no fa.
POP3 només té avantatge si vols llegir el correu sense connexió o tens un sol equip.



### 3. Etiqueta «institut» en color verd


<img width="1366" height="768" alt="Captura de pantalla 2026-11-26 191942(1)" src="https://github.com/user-attachments/assets/31157b52-f95e-457f-be9d-001113c65f2c" />


### 4. Filtres

| Filtre | Criteri | Acció |
|---|---|---|
| 1 | `puig` | Aplica l'etiqueta «institut» |
| 2 | `publicitat` | Aplica l'etiqueta «promocions» i omet la safata d'entrada |
| 3 | Professor 1 | Marca'l com a important |
| 4 | Professor 2 | Marca'l com a important |
| 5 | Altres (`examen`, `moodle`) | Aplica l'etiqueta «institut» |


<img width="1366" height="768" alt="Captura de pantalla 2026-11-26 200358" src="https://github.com/user-attachments/assets/9a26cfb0-35c0-40ee-bcc3-89e9b9b52f97" />


### 5. Resposta automàtica de vacances

Missatge configurat: **«Estic de vacances!»**


<img width="1366" height="768" alt="Captura de pantalla 2026-11-26 200923" src="https://github.com/user-attachments/assets/6e435942-19b7-4da3-952c-dc2c04a762ae" />


---

## Fase 2: comprovar l'accés

### 1. Accés IMAP i paràmetres de cada servei

L'accés IMAP està **activat**.


<img width="1366" height="768" alt="Captura de pantalla 2026-11-26 202110" src="https://github.com/user-attachments/assets/dd6a3f5b-84af-4a57-a58d-6fffef0e4ec8" />


| Servei | Servidor | Port | Seguretat | Usuari |
|---|---|---|---|---|
| IMAP (entrada) | imap.gmail.com | 993 | SSL/TLS | adreça de correu completa |
| POP3 (entrada) | pop.gmail.com | 995 | SSL/TLS | adreça de correu completa |
| SMTP (sortida) | smtp.gmail.com | 465 (SSL) o 587 (STARTTLS) | SSL/TLS o STARTTLS |


### 2. Missatge entre dos comptes

Amb dues sessions obertes, el company envia un correu amb la paraula «puig» i arriba amb l'etiqueta verda «institut».


<img width="1920" height="1080" alt="Captura de pantalla de 2026-11-27 09-35-01" src="https://github.com/user-attachments/assets/25fe4ab0-2ba4-4f1e-8160-18cb023ed112" />



### 3. Resposta

He respost al missatge i la resposta torna al company.


<img width="1920" height="1080" alt="Captura de pantalla de 2026-11-27 09-36-21" src="https://github.com/user-attachments/assets/eb11d270-dfbd-4fcb-9330-7f0bca8a132d" />


### 4. SPF, DKIM i DMARC

<img width="1920" height="1080" alt="Captura de pantalla de 2026-11-27 09-46-06" src="https://github.com/user-attachments/assets/6200bb48-84f4-4869-9313-86b925f31682" />


| Capçalera | Què comprova | Resultat |
|---|---|---|
| SPF | Que el servidor que envia el correu està autoritzat pel domini del remitent | PASS |
| DKIM | Que el missatge porta una signatura digital del domini i no s'ha modificat pel camí | PASS |
| DMARC | La política del domini: què fer si SPF o DKIM fallen | FAIL |

El DMARC dona **FAIL** perquè la signatura DKIM usa el domini genèric de Google (`gappssmtp.com`) i no `elpuig.xeill.net`, de manera que no està alineada amb el domini del remitent. Això indica que el domini del centre no té DKIM propi configurat. El missatge va arribar igualment, així que la política DMARC del domini no el rebutja ni l'aïlla.


### 5. Llista de proves

| # | Prova | Resultat esperat | Resultat obtingut | OK |
|---|---|---|---|---|
| 1 | Accés IMAP activat | IMAP habilitat | IMAP actiu | ✔ |
| 2 | Enviar correu entre comptes | Arriba a la bústia | Arriba | ✔ |
| 3 | Correu amb «puig» | Etiqueta «institut» | Etiqueta aplicada | ✔ |
| 4 | Etiqueta «institut» | Color verd | Verd | ✔ |
| 5 | Correu amb «publicitat» | A «promocions», sense passar per Rebuts | A «promocions» | ✔ |
| 6 | Correu del professor 1 | Marcat com a important | Marcat (provat amb el compte d'un company) | ✔ |
| 7 | Correu del professor 2 | Marcat com a important | Marcat (provat amb el compte d'un company) | ✔ |
| 8 | Resposta automàtica | El remitent rep «Estic de vacances!» | Rebut | ✔ |
| 9 | Respondre a un missatge | La resposta torna al remitent | Tornada | ✔ |
| 10 | SPF a l'original | PASS | PASS | ✔ |
| 11 | DKIM a l'original | PASS | PASS (gappssmtp.com) | ✔ |
| 12 | DMARC a l'original | PASS | FAIL (DKIM no alineat) | ✘ |



<img width="1920" height="1080" alt="Captura de pantalla de 2026-11-27 13-51-29" src="https://github.com/user-attachments/assets/ba4b5d30-6c29-42d7-8632-ddfa7885f960" />

<img width="1920" height="1080" alt="Captura de pantalla de 2026-11-27 13-52-25" src="https://github.com/user-attachments/assets/cc6de8a6-4e39-49af-a318-63ad6c929bf7" />


<img width="1920" height="1080" alt="Captura de pantalla de 2026-11-27 09-41-32" src="https://github.com/user-attachments/assets/9f7e6802-4d8f-4a40-a675-4f05a3ce7265" />


---

## Fase 3: el viatge

### 1. Ruta a Google Maps

Ruta de 7 dies: Barcelona → Santo Domingo → Bayahíbe → Punta Cana → Barcelona.

| Dia | Parada | Transport |
|---|---|---|
| 1 | Barcelona → Santo Domingo | Avió |
| 2 | Santo Domingo | A peu |
| 3 | Santo Domingo → Bayahíbe | Guagua |
| 4 | Bayahíbe (Illa Saona) | Barca |
| 5 | Bayahíbe → Punta Cana | Autobús |
| 6 | Punta Cana | A peu / taxi |
| 7 | Punta Cana → Barcelona | Avió |

Enllaç al mapa:https: //www.google.com/maps/d/edit?mid=1ts3PSSrds0m0aTCbdJV1EVxzeb93EMk&usp=sharing


<img width="1366" height="768" alt="Captura de pantalla 2026-11-26 224921" src="https://github.com/user-attachments/assets/f3488bdd-b4ef-4b42-b193-71828fa20ebc" />


### 2. Pressupost al full de càlcul

Enllaç al full: https://docs.google.com/spreadsheets/d/1GeO7hbcIWQsF_0O3ACywYzaBpknP1-D2dTtkarr8Oe8/edit?usp=sharing


| Concepte | Import |
|---|---|
| Transport | 860 € |
| Allotjament | 270 € |
| Menjar | 175 € |
| **Total** | **1.305 €** |


La cel·la de resultat usa la funció `IF`:

```
=IF(B5<=B6; "Dins del pressupost"; "T'has passat")
```

`IF` té tres parts: una condició, què passa si és certa i què passa si no ho és. Aquí compara el total (B5) amb el límit de 1.500 € (B6) i mostra si el pressupost s'ha respectat.


