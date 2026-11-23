# TiDiDesk Build

Repo pubblica di Tastiere Digitali che **compila soltanto** i client RustDesk personalizzati. È un fork di [bryangerlach/rdgen](https://github.com/bryangerlach/rdgen), e da lì prende ogni giorno gli aggiornamenti.

- Il generatore vero (server, login, aggiornamenti dei client) sta nella repo privata `tastieredigitali/TiDiDesk`: è lui a lanciare queste build.
- I programmi compilati **non escono da qui**: niente release e niente artifact. Ogni build li manda soltanto al server TiDiDesk, insieme al token di quella build. La configurazione arriva cifrata.
- Le modifiche fatte da TD riguardano solo i workflow. In `generator-windows.yml` c'è la firma Azure Artifact Signing, che usa i secret dell'organizzazione. In `generator-macos.yml` c'è la versione del bundle, che serve all'aggiornamento automatico.
- Secret di questa repo: `GENURL` e `ZIP_PASSWORD`, gli stessi valori dello stack TiDiDesk.
