# Nest.js
## Introduzione
Nest (NestJS) è un framework per la creazione di applicazioni Node.js lato server efficienti e scalabili. Utilizza JavaScript progressivo, è sviluppato con TypeScript e lo supporta pienamente (pur consentendo agli sviluppatori di programmare in JavaScript puro) e combina elementi di OOP (Programmazione Orientata agli Oggetti), FP (Programmazione Funzionale) e FRP (Programmazione Funzionale Reattiva).

Nest si avvale di robusti framework HTTP Server come **Express** (predefinito).

Nest offre un livello di astrazione superiore rispetto ai comuni framework Node.js (Express/Fastify), ma espone anche le loro API direttamente allo sviluppatore. Questo offre agli sviluppatori la libertà di utilizzare la miriade di moduli di terze parti disponibili per la piattaforma sottostante.

## Installazione e Setup

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

A questo punto il progetto sarà creato e inizializzato. Per runnare la nostra applicazione nestjs entro nella cartella creata e digito il comando:
```
npm run start
```
Se voglio runnare l'applicazione e vedere tutti i log:
```
npm run start:dev
```
## Struttura del progetto
### Componenti di default
Quando creo il progetto, si crea una struttura di default che contiene una directory src:
```
src
   -  app.controller.spec.ts
   -  app.controller.ts
   -  app.module.ts
   -  app.service.ts
   -  main.ts
```
Guardiamo nello specifico i file creati.

- **app.controller.spec.ts**: Un controller di base con un singolo percorso.
```
import { Test, TestingModule } from '@nestjs/testing';
import { AppController } from './app.controller';
import { AppService } from './app.service';

describe('AppController', () => {
  let appController: AppController;

  beforeEach(async () => {
    const app: TestingModule = await Test.createTestingModule({
      controllers: [AppController],
      providers: [AppService],
    }).compile();

    appController = app.get<AppController>(AppController);
  });
```

- **app.controller.ts**: Le unità di test per il controller.
```
import { Controller, Get } from '@nestjs/common';
import { AppService } from './app.service';

@Controller()
export class AppController {
  constructor(private readonly appService: AppService) {}

  @Get()
  getHello(): string {
    return this.appService.getHello();
  }
}
```

- **app.module.ts**: Il modulo principale dell'applicazione (root)
```
import { Module } from '@nestjs/common';
import { AppController } from './app.controller';
import { AppService } from './app.service';

@Module({
  imports: [],
  controllers: [AppController],
  providers: [AppService],
})
export class AppModule {}
```

- **app.service.ts**: Un servizio di base con un solo metodo.
```
import { Injectable } from '@nestjs/common';

@Injectable()
export class AppService {
  getHello(): string {
    return 'Hello World!';
  }
}
```

- **main.ts**: Il file di ingresso dell'applicazione che utilizza la funzione principale NestFactory per creare un'istanza dell'applicazione Nest.
```
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  await app.listen(process.env.PORT ?? 3000);
}
bootstrap();
```
NestFactory espone alcuni metodi statici che consentono di creare un'istanza dell'applicazione.
Nell'esempio main.ts sopra, avviamo semplicemente il nostro listener HTTP, che consente all'applicazione di attendere le richieste HTTP in ingresso.

### Componenti aggiuntivi
Se voglio creare un altro modulo sotto la cartella src 
```
nest g module module-name
```
Questo comando andrà a creare il file module-name.modules.ts sotto la cartella module-name. 
```
src
   - module-name
         - module-name.modules.ts
   -  app.controller.spec.ts
   -  app.controller.ts
   -  app.module.ts
   -  app.service.ts
   -  main.ts
```

Quando aggiungo un nuovo modulo, questo verrà aggiunto in automatico negli import di app.modules.ts, che costituisce il modulo principale.

Se voglio aggiungere un controller sotto la cartella module-name:

```
nest g controller module-name
```
A questo punto il progetto avrà struttura:
```
src
   - module-name
         - module-name.modules.ts
         - module-name.controller.spec.ts
         - module-name.controller.ts
   -  app.controller.spec.ts
   -  app.controller.ts
   -  app.module.ts
   -  app.service.ts
   -  main.ts
```
Allo stesso modo, se voglio aggiungere un servizio:
```
nest g service module-name
```
La struttura del progetto sarà quindi:
```
src
   - module-name
         - module-name.modules.ts
         - module-name.controller.spec.ts
         - module-name.controller.
         - module-name.service.spec.ts
         - module-name.service.ts
   -  app.controller.spec.ts
   -  app.controller.ts
   -  app.module.ts
   -  app.service.ts
   -  main.ts
```
### Linting e Formattazione
Un progetto Nest viene fornito con un linter di codice e un formattatore preinstallati (rispettivamente eslint e prettier).
```
# Lint and autofix with eslint
$ npm run lint

# Format with prettier
$ npm run format
```
## Componenti principali
### 1. Controllers
Un controller riceve le richieste HTTP dal client (GET, POST, ecc.), chiama la logica dai services, e restituisce la risposta al client. 

Ogni controller deve gestire delle specifiche richieste; il meccanismo di routing decide a quale controller passare la richiesta. 

Per creare un controller, si usa una classe TypeScript decorata con @Controller()



### 2. Providers


### 3. Modules



### 4. Middleware


### 5. Exception Filters


### 6. Pipes


### 7. Guards


### 8. Interceptors


### 9. Custom Decorators
