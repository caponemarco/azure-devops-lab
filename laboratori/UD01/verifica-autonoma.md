# Verifica Autonoma — UD01: Preparazione dell'ambiente e metodo di lavoro

## Nota Tecnica dell'Ambiente

L'analisi dell'ambiente locale conferma che la distribuzione Ubuntu è in esecuzione su WSL 2 (verificata da PowerShell tramite `wsl --list --verbose`, dove la colonna VERSION riporta il valore 2).

L'accesso al repository locale posizionato nel percorso Linux `/home/marco/workspace/azure-devops-lab` mostra il corretto puntamento alla radice del progetto, verificato sia con `pwd` sia tramite `git rev-parse --show-toplevel`. La configurazione del remote punta all'URL pubblico `https://github.com/caponemarco/azure-devops-lab.git` associato all'account GitHub. Nella sezione *Settings -> Collaborators* del repository remoto, l'invito inviato al docente risulta in stato Pending.

In un flusso di lavoro Git, la **working tree** è la cartella di lavoro locale dove si modificano i file; la **staging area** (index) raccoglie le modifiche selezionate con `git add` pronte per il salvataggio; il **commit locale** registra lo snapshot nello storico Git; il **repository remoto** sincronizza i commit online tramite `git push`.

Per verificare Azure CLI si utilizza `az version`. Un tipico errore di contesto si verifica eseguendo comandi Git fuori dal repository (`fatal: not a git repository`), individuabile cercando la cartella `.git` con `find ~/workspace -maxdepth 3 -type d -name .git -print`.

---

## Autovalutazione

| Capacità | Valutazione |
| :--- | :--- |
| Distinguo PowerShell dal terminale Ubuntu | Completato |
| Verifico che Ubuntu utilizzi WSL 2 | Completato |
| Riconosco la radice del repository Git | Completato |
| Verifico il remote prima del push | Completato |
| Distinguo file non tracciato e file in staging | Completato |
| Inserisco in staging soltanto il file richiesto | Completato |
| Verifico lo stesso commit in locale e su GitHub | Completato |
| Verifico lo stato dell'invito al docente | Completato |
| Riconosco ed escludo dati riservati | Completato |

---

## Parte A — Scelte operative

1. **B.** Windows e Ubuntu possono possedere installazioni distinte di Git.
2. **C.** `wsl --list --verbose`
3. **C.** Per lavorare nel file system Linux, più adatto al successivo workflow con Docker e bind mount.
4. **C.** Verificarne il funzionamento e proseguire senza reinstallazione.
5. **A.** Il commit esiste localmente, ma non è ancora stato eseguito `git push`.
6. **A.** `git status` dopo `git add`
7. **C.** Usarlo nella pagina di autenticazione e non conservarlo nel repository.
8. **B.** L'indicatore WSL: Ubuntu e un terminale con percorso Linux.
9. **C.** Per partecipare alle attività di scrittura, revisione e collaborazione previste dal percorso.

---

## Parte B — Risposte brevi

**10. Differenza fra Git e GitHub:**
Git è il sistema di controllo versione distribuito locale (CLI) per tracciare le modifiche al codice. GitHub è la piattaforma Cloud remota per ospitare i repository, facilitando la condivisione e la collaborazione tra sviluppatori.

**11. Sequenza minima di comandi:**
```bash
# OSSERVARE LE MODIFICHE: mostra lo stato dei file nel working tree e in staging
git status

# PREPARARE UN SINGOLO FILE: aggiunge il file alla staging area
git add laboratori/UD01/verifica-autonoma.md

# CREARE UN COMMIT: registra lo snapshot locale con un messaggio descrittivo
git commit -m "Documenta la verifica autonoma dell'ambiente"

# INVIARE AL REMOTE: trasmette i commit locali al repository su GitHub
git push