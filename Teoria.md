## Docker	
piattaforma che consente di creare, distribuire ed eseguire container. Utilizzando Docker, gli sviluppatori possono impacchettare applicazioni e tutte le loro dipendenze in un container isolato, che può essere eseguito in qualsiasi ambiente, senza preoccuparsi delle differenze tra sistemi operativi o configurazioni. Docker semplifica la gestione e l'esecuzione dei container, fornendo strumenti per creare immagini (versioni "congelate" di un'applicazione), avviare container e gestirne il ciclo di vita. Inoltre, grazie alla sua capacità di automatizzare il processo di configurazione, Docker migliora la portabilità delle applicazioni e la consistenza tra i vari ambienti, dalla fase di sviluppo alla produzione.
### Dockerfile
file di testo che contiene una serie di istruzioni utilizzate per creare un'immagine Docker. Ogni istruzione nel Dockerfile rappresenta un layer nell'immagine finale e può includere comandi per installare software, copiare file, impostare variabili d'ambiente, e definire quale comando eseguire quando il container viene avviato.
## Kubernetes
piattaforma open-source per la gestione e l'orchestrazione di applicazioni containerizzate. Permette di distribuire, scalare e gestire container su un insieme di nodi, che insieme formano un cluster (oltre ai nodi il cluster contiene un’istanza chiamata control plane con lo scopo di gestire i nodi). Ogni nodo è un'istanza di calcolo che esegue i container. Un'unità minima di esecuzione in Kubernetes è il Pod, che può contenere uno o più container. Di solito, un Pod ospita un solo container, ma può anche contenerne di più se questi hanno dipendenze strette tra loro, condividendo risorse come la rete e lo storage.
Per gestire la disponibilità e la scalabilità delle applicazioni, Kubernetes utilizza il Deployment, che è un gruppo di replica di Pod. I Deployment mantengono i Pod attivi anche in caso di guasti e gestiscono il numero di repliche in esecuzione. Per garantire l'accesso ai container, Kubernetes crea un Service con un indirizzo IP fisso, che può essere esposto tramite un load balancer esterno. Questo consente di accedere ai Pod anche dall'esterno del cluster.

## Riassumendo
Docker è una piattaforma che consente di costruire, eseguire e gestire container.
- I container Docker sono utilizzati per eseguire applicazioni in modo isolato, impacchettando l'applicazione e tutte le sue dipendenze in un'unica unità.
- Docker gestisce principalmente il ciclo di vita dei container su una singola macchina (locale o virtuale).
     				
Kubernetes è una piattaforma open-source per l'orchestrazione dei container.
- Gestisce l'esecuzione di container Docker (e di altri tipi di container) su larga scala, coordinando il deployment, la scalabilità e la gestione dei container su più nodi in un cluster.
- Kubernetes è progettato per gestire container su più server, fornendo funzionalità avanzate come l'auto-ripristino, il load balancer, la gestione del traffico e la distribuzione continua.
