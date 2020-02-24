# 01 - Le basi di Git

### Premessa
In questa sezione si da per scontato che sia già installato il programma git e si abbia un account su GitHub, come riportato al capitolo XX.
Tutti i comandi saranno dati da terminale (prompt dei comandi, shell, o altro modo che avremo imbastito)

### Creare un repository git sulla proprio computer

Quando stiamo per iniziaiare u nnuovo progetto sul proprio computer locale che si vorrà poi esportare, bisogna creare un repository ('repo' in gergo).
Una volta che ci saremo posizionati nella cartella con il nome del del progetto, daremo il comando:
```bash
git init
```
Questo comando genera una cartella nascosta .git al cui interno ci sono tutti i file necessari a git per sapere come procedere nei passi successivi.

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

In pratica ci dice che si è accorto che esiste un nuovo file di nome nuovofile.txt, ma a meno di usare il comando git add non succederà noiente.
