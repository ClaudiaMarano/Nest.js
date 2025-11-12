# Nest.js
## Introduzione
Nest (NestJS) è un framework per la creazione di applicazioni Node.js lato server efficienti e scalabili. Utilizza JavaScript progressivo, è sviluppato con TypeScript e lo supporta pienamente (pur consentendo agli sviluppatori di programmare in JavaScript puro) e combina elementi di OOP (Programmazione Orientata agli Oggetti), FP (Programmazione Funzionale) e FRP (Programmazione Funzionale Reattiva).

Nest si avvale di robusti framework HTTP Server come **Express** (predefinito).

Nest offre un livello di astrazione superiore rispetto ai comuni framework Node.js (Express/Fastify), ma espone anche le loro API direttamente allo sviluppatore. Questo offre agli sviluppatori la libertà di utilizzare la miriade di moduli di terze parti disponibili per la piattaforma sottostante.

## Installazione

Download Node.js per Windows:
```
https://nodejs.org/en/download
```
Durante l'installazione, ricorda di aggiungere nodejs al path. Inoltre, in fase di installazione verrà richiesto più volte in powershell di premere enter per installare tutte le dipendenze necessarie. Attendi finchè l'installazione non sarà conclusa (potrebbero volerci diversi minuti). A questo punto, verifica l'installazione da terminale:

```
node -v
```
Se nodejs è correttaemente installato, procediamo alla creazione di una cartella e poniamoci in VS Code. 

Adesso installiamo globalmente la CLI per Nodejs:
```
npm i -g @nestjs/cli
```

Creiamo un nuovo progetto con il comando:
```
nest new project-name
```
Dopo questo comando, mi viene chiesto quale package manager vogliamo usare; selezioniamo npm.
