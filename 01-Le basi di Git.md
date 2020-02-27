# 01 - Le basi di Git

### Premessa
In questa sezione si da per scontato che sia già installato il programma git e si abbia un account su GitHub, come riportato al capitolo XX.
Tutti i comandi saranno dati da terminale (prompt dei comandi, shell, o altro modo che avremo imbastito)

### Creare un repository git sulla proprio computer

Quando stiamo per iniziaiare un nuovo progetto sul proprio computer locale che si vorrà poi esportare, bisogna creare un repository ('**repo**' in gergo).
Una volta che ci saremo posizionati nella cartella con il nome del del progetto, daremo il comando:

**`git init`**

Questo comando genera una cartella nascosta *.git* al cui interno ci sono tutti i file necessari a git per sapere come procedere nei passi successivi.

### Aggiungere un nuovo file al repo

Adeso abbiamo una cartella col nome del progetto ed una sotto cartella (nascosta) con i file necessari di git.
Iniziamo ad aggiungere un file in questa cartella.
Potrà essere qualcosa di più concreto creato con il nostro editor preferito o anche un banale:
```bash
echo "Ciao!" > nuovofile.txt
```
tanto per fare un esempio ed avere un file su cui lavorare.
Quando avremo preso pratica potremo aggiungere anche cartelle e tanti bei files.
Aver aggiunto un nuovo file alla cartella del repository non vuol dire che git ne sia a conoscenza e tanto meno cosa debba farci.
Come esempio vediamo cosa sa git di quello che abbiamo fatto e digitiamo
```bash
git status
```
la risposta che otteremo sara qualcosa del tipo

```console
On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        nuovofile.txt

nothing added to commit but untracked files present (use "git add" to track)
```

In pratica ci dice che si è accorto che esiste un nuovo file di nome *nuovofile.txt*, ma a meno di usare il comando **git add** non succederà niente.

### Preparare il file per essere gestito

Dopo aver creato il nuovo file nel nostro ***repository*** locale, bisogna far si che sia gestito da git.
Dobbiamo quindi preparare l'ambiente gestito da git per eleaborare il nostro file, ovvero aggiungerlo con il comando 
```bash
git add nuovofile.txt
```
alla fase di staging (letteralmente staging = messa in scena, ovvero pronto per lo *"spettacolo"* di git).

Dopo l'esecuzione di **`git add`** potremmo avere dei messaggi. Uno tipico è la conversione del codice di ritorno a capo a seconda che si sia in ambiente Windows o Linux. Ecco un esempio di output in ambiente Windows dove il fine riga è LF invece di CR+LF.
```console
warning: LF will be replaced by CRLF in nuovofile.txt.
The file will have its original line endings in your working directory
```
Lo staging è una fase temporanea da cui devono passare i nuovi file prima di essere elaborati da git, questo perchè potrebbe volere processare solo alcuni file) e altri mantenerli solo nella directoryy locale come appunti o altro, ma non come parte del progeto.

Avendo un solo file per il momento il comando **`git add`** avrà preparato quello, quindi riesequendo il comando **`git status`** adesso otterremo:
```console
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   nuovofile.txt
```
Si noti il messaggio **Changes to be committed** quindi il nostro file è stato aggiunto ed è pronto per essere gestito da git.
Nell'output sopra riportato ci viene suggerito anche come poter fare per rimuovere il file dallo stato di *stagging*.

***NOTA*** per aggiungere più di un file, bisogna specificarli uno per uno separati da uno spazio oppure usare il carattere punto **`git add .`** per aggiungere tutti quelli presenti nella cartella corrente che ancora non sono nella fase di *staging*.

### Effettuare il commit

Adesso che il file è pronto, possiamo effettuare il commit ovvero inserirlo nel **nostro** *repository* locale.
Eseguiamo il comando coi parametri:
```bash
git commit -m "messaggio di commento al commit"
```
Proviamo a fare il nostro primo *commit*
```console
$ git commit -m "Inizio commit"
[master bc068b2] Inizio commit
 1 file changed, 1 insertion(+)
 create mode 100644 nuovofile.txt
```
In questo caso, essendo un tutorial, è stato messo un messaggio di esempio, ma in realtà il messaggio da mettere dovrebbe essere qualcosa che riguardi il file.

Potrebbe essere l'inizio del progetto come nel esempio o il riferimento a qualche modifica, alla correzione di un bug o di un semplice refuso e così via.

Evitare messaggi privi di senso o incomprensibili, impedirebeb ad altri utenti, ma anche a noi stessi in un secondo momento, di capire il perchè di tale azione.

Inoltre il lavoro fatto verrebbe visto degli altri utenti come molto poco collaborativo e triste.
Ovviamente è consigliato usare l'inglese per poter rendere comprensibile a più persone possibili ed il messaggio dovrebbe essere il più sintetico possibile, ma comprensibile.

***Attenzione*** stiamo sempre lavorando sul nostro repository locale, non abbiamo avuto alcun contatto con il server remoto.
