# Comandi Essenziali di Kubernetes

## Gestione dei Manifests YAML

```
kubectl apply -f <file>.yaml      # Crea o aggiorna una risorsa da un file YAML
kubectl delete -f <file>.yaml     # Elimina una risorsa definita in un file YAML
```

## Gestione dei Pod

```
kubectl get pods                             # Elenca tutti i pod nel namespace corrente
kubectl get pods -A                          # Elenca tutti i pod in tutti i namespace
kubectl describe pod <pod-name>              # Mostra dettagli su un pod specifico
kubectl logs <pod-name>                      # Visualizza i log di un pod
kubectl logs -f <pod-name>                   # Mostra i log in tempo reale
kubectl exec -it <pod-name> -- <command>     # Esegue un comando in un pod
kubectl delete pod <pod-name>                # Elimina un pod specifico
```

## Gestione dei Deployment

```
kubectl get deployments                                     # Mostra tutti i deployment
kubectl describe deployment <deployment-name>               # Mostra dettagli su un deployment
kubectl create deployment <name> --image=<image>            # Crea un nuovo deployment
kubectl scale deployment <name> --replicas=<num>            # Modifica il numero di repliche
kubectl rollout restart deployment <name>                   # Riavvia il deployment
kubectl edit deployment <name>                              # Apre lo YAML del deployment
kubectl delete deployment <name>                            # Elimina un deployment
```

## Gestione dei Servizi

```
kubectl get services                                         # Mostra tutti i servizi esistenti
kubectl describe service <service-name>                      # Mostra dettagli su un servizio
kubectl expose deployment <name> --type=<type> --port=<port> # Espone un deployment come servizio
kubectl delete service <service-name>                        # Elimina un servizio
```

## Gestione dei Namespace

```
kubectl get namespaces                                             # Elenca tutti i namespace
kubectl create namespace <namespace>                               # Crea un nuovo namespace
kubectl delete namespace <namespace>                               # Elimina un namespace
kubectl config set-context --current --namespace=<nome-namespace>  # Imposta il namespace corrente
```

## Gestione dei ConfigMap e Secret

```
kubectl get configmaps                                        # Mostra tutti i ConfigMap
kubectl create configmap <name> --from-literal=KEY=VALUE      # Crea un ConfigMap da una variabile
kubectl delete configmap <name>                               # Elimina un ConfigMap

kubectl get secrets                                           # Mostra tutti i Secret
kubectl create secret generic <name> --from-literal=KEY=VALUE # Crea un Secret
kubectl delete secret <name>                                  # Elimina un Secret
```

## Debugging e Monitoraggio

```
kubectl get events   # Mostra gli eventi del cluster
kubectl top pod      # Mostra l'utilizzo delle risorse dei pod
kubectl top node     # Mostra l'utilizzo delle risorse dei nodi
```

---

# Comandi Essenziali Docker

## Gestione delle Immagini

```
docker images                            # Mostra le immagini Docker locali
docker pull <image>                      # Scarica un'immagine dal Docker Hub
docker rmi <image>                       # Rimuove un'immagine dal sistema
docker build -t <image-name>:<tag> .     # Crea un'immagine da un Dockerfile
```

## Push delle Immagini (Artifact Registry)

```
gcloud auth configure-docker <region>-docker.pkg.dev
# Configura l'autenticazione Docker per Artifact Registry

docker tag <image-name>:<tag> <region>-docker.pkg.dev/<project-id>/<repo-name>/<image-name>:<tag>
# Tagga l'immagine

docker push <region>-docker.pkg.dev/<project-id>/<repo-name>/<image-name>:<tag>
# Effettua il push nel repository
```

## Gestione dei Container

```
docker run <image>                                         # Crea e avvia un container
docker run -d <image>                                      # Avvia in background (detached)
docker run -p <host-port>:<container-port> <image>         # Mappa porte
docker run --name <name> <image>                           # Assegna un nome al container
docker ps                                                  # Mostra i container attivi
docker ps -a                                               # Mostra tutti i container
docker stop <container>                                    # Ferma un container
docker rm <container>                                      # Rimuove un container
docker restart <container>                                 # Riavvia un container
```

## Debugging e Controllo

```
docker logs -f <container>                  # Mostra i log in tempo reale
docker inspect <container>                  # Mostra dettagli del container
docker exec -it <container> <command>       # Esegue un comando all'interno del container
docker exec -it <container> bash            # Accede alla shell del container
docker stats                                # Mostra l’uso delle risorse
```

## Gestione dei Volumi e Reti

```
docker volume ls                             # Mostra i volumi
docker volume create <volume-name>           # Crea un volume

docker network ls                            # Mostra le reti Docker
docker network create <network-name>         # Crea una nuova rete
```

## Pulizia del Sistema

```
docker system prune                          # Rimuove risorse inutilizzate
docker rmi $(docker images -q)               # Cancella tutte le immagini
docker rm $(docker ps -aq)                   # Cancella tutti i container
```

## Pubblicazione su un Registry

```
docker tag <old-image>:<old-tag> <new-repository>/<new-image-name>:<new-tag>
# Tag per push

docker push <repository>/<image>:<tag>         # Push su registry
docker pull <repository>/<image>:<tag>         # Pull da registry
```
---

# Comandi Fondamentali Dockerfile

## Definizione dell'Immagine Base

```
FROM <image>:<tag>        # Specifica l'immagine base da cui partire
```

## Gestione della Directory di Lavoro

```
WORKDIR <path>            # Imposta la directory di lavoro all'interno del container
```

## Copia e Aggiunta di File

```
COPY <src> <dest>         # Copia file o directory dalla macchina host al container
ADD <src> <dest>          # Simile a COPY, ma supporta file compressi e URL
```

## Esecuzione di Comandi Durante la Build

```
RUN <command>             # Esegue un comando durante la creazione dell'immagine
```

## Definizione del Comando di Avvio

```
CMD ["executable", "arg1", "arg2"]         # Comando eseguito quando il container parte
ENTRYPOINT ["executable", "arg1", "arg2"]  # Definisce il comando principale, permette argomenti extra
```

## Esposizione delle Porte

```
EXPOSE <port>             # Indica quale porta il container userà
```

## Impostazione di Variabili d'Ambiente

```
ENV key=value             # Definisce una variabile d'ambiente nel container
```

## Etichettatura dell'Immagine

```
LABEL key=value           # Aggiunge metadati all'immagine
```

## Definizione di un Volume

```
VOLUME ["/data"]          # Crea un volume per la persistenza dei dati
```

## Impostazione di un Utente per l'Esecuzione

```
USER <username>           # Esegue i comandi con un utente specifico invece di root
```
