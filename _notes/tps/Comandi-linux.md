---
title: Comandi comuni in linux
tags: Tps,Linux,Shell,Terminale
toc: true
season: winter
---

# Introduzione

Nei sistemi basati su unix, il terminale è il programma che ci permette di visualizzare a video una shell (generalmente bash, ma può essere anche sh, zsh, chs, fish). È lei che gestisce i comandi e ci permette di eseguirli.

Va inoltre notato che linux, a differenza di windows, è case-sensitive, cioè differenzia le maiuscole con le minuscole. Quindi un file chiamato `testo` sarà diverso da un file chiamato `TeStO`.

## Argomenti di un comando

Di solito i comandi accettano argomenti per definire il proprio comportamento. Molti di questi seguono un preciso schema:

- Se l'argomento può essere rappresentato da una lettera si utilizza `-` (per esempio l'argomento a per il comando `ls`: `ls -a`). Essi si possono concatenare senza ripetere il trattino (`ls -al` è uguale a `ls -a -l`);
- Se l'argomento viene rappresentato con più lettere si utilizza `--` e non possono essere concatenati.

## Codici di uscita

Ogni programma, al termine della sua esecuzione, restituisce un codice che rappresenta l'uscita e il ritorno alla shell.

Generalmente questo numero non viene visualizzato automaticamente.

Con un'esecuzione senza errori il codice sarà `0`, se invece si sarà incontrato un errore il codice rappresenterà quell'errore. È dunque necessario consultare la documentazione relativa al programma per capire di che errore si tratta.  

## Pagine man

Quasi ogni comando/programma (soprattutto quelli preinstallati) offrono un comodo metodo per consultare un manuale.

Per visualizzare il manuale del comando `ls`, per esempio, basterà digitare:

```bash
man ls
```

Per ulteriori informazioni è possibile consultare il manuale di `man`:

```bash
man man
```



# Navigazione nel filesystem

## Struttura del filesystem

In linux tutto è un file, pure i dispositivi collegati come mouse e tastiera. Le directory sono dei file speciali che contengono altri file.

Tutte le cartelle partono dalla _root directory_, ovvero `/`, e per rappresentare un percorso le cartelle vengono separate anch'esse da `/`.

Per esempio la cartella `documenti` nella home dell'utente `giulio` (`/home/giulio/`) avrà come percorso:

```
/home/giulio/documenti
```

Ma se ci si troverà già nella home, il percorso potrà essere espresso in modo relativo come:

```
documenti
```

Per indicare la cartella attuale si può utilizzare `.`, per indicare la cartella genitore (quella appena prima) si utilizza `..` e per indicare la cartella home dell'utente attuale `~`.

### File nascosti

Per nascondere un file o una directory si utilizza `.` davanti al nome.

Per esempio `.testo.png` è un file nascosto.

### Gerarchia

I file sono generalmente organizzati secondo una precisa gerarchia:

- **/bin**: file eseguibile per il sistema;
- **/boot**: file necessari per il processo di boot;
- **/dev**: dispositivi fisici (harddisk, tastiere, microfoni, ...);
- **/etc**: file di configurazione locali alla macchina;
- **/home**: contiene le cartelle home degli utenti;
- **/media**: generalmente vengono montati dispositivi rimovibili (gestita dal sistema);
- **/mnt**: utilizzata per montare dispositivi;
- **/proc**: contiene i processi del sistema;
- **/root**: home dell'utente root;
- **/tmp**: file temporanei, viene montata in RAM;
- **/usr**: file di sistema relativi agli utenti;

Per una lista più esaustiva utilizzare il comando:

```bash
man hier
```



## ls

Il comando `ls` (diminutivo di _list_) visualizza il contenuto di una directory.

```bash
ls /home/giulio
```

Se invocato senza argomento utilizza la directory attuale.

### -R

```bash
ls -R
```

Visualizza il contenuto delle sottodirectory in modo ricorsivo.

### -a

```bash
ls -a
```

Visualizza anche i file nascosti.

### -l

```bash
ls -l
```

Visualizza informazioni aggiuntive riguardanti i file.

Con `-h` le dimensioni saranno rappresentate con una scala adeguata e non in byte.

## pwd

Il comando `pwd` (acronimo di _print working directory_) visualizza la cartella in cui ci troviamo.

## cd

Il comando `cd` (acronimo di _change directory_) ci permette di cambiare la cartella in cui ci troviamo.

```bash
cd /home/giulio/documenti
```

Se non viene fornito un percorso utilizza la cartella home.

# Lavorare con i file

**TODO: finire**