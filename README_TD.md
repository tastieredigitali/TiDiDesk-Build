# TiDiDesk Build

Repo pubblica di Tastiere Digitali che **compila soltanto** i client RustDesk personalizzati. È un fork di [bryangerlach/rdgen](https://github.com/bryangerlach/rdgen), e da lì prende ogni 6 ore gli aggiornamenti.

- Il generatore vero (server, login, aggiornamenti dei client) sta nella repo privata `tastieredigitali/TiDiDesk`: è lui a lanciare queste build.
- I programmi compilati **non escono da qui**: niente release e niente artifact. Ogni build li manda soltanto al server TiDiDesk, insieme al token di quella build. La configurazione arriva cifrata.
- Le modifiche fatte da TD riguardano solo i workflow. In `generator-windows.yml` c'è la firma Azure Artifact Signing, che usa i secret dell'organizzazione, e si fa solo l'exe (niente MSI). TiDiDesk lancia solo la build Windows: il workflow Mac resta ma non viene usato. In `generator-macos.yml` c'è la versione del bundle, che serve all'aggiornamento automatico, e il numero di versione si scrive con perl perché il sed del Mac rompeva Cargo.lock. In `generator-windows.yml`, `generator-macos.yml` e `bridge.yml` il passo «TD: versioni degli strumenti prese da RustDesk» legge dal workflow di RustDesk della versione scelta Flutter, Rust, vcpkg e NDK, così una versione nuova di RustDesk si compila con i suoi strumenti anche se rdgen non si è ancora aggiornato.
- Secret di questa repo: `GENURL` e `ZIP_PASSWORD`, gli stessi valori dello stack TiDiDesk.
