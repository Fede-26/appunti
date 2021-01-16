---
title: Comandi comuni in linux
date: 2021-01-15T15:15:21+01:00
draft: false
---

# Introduzione

Nei sistemi basati su unix, il terminale è il programma che ci permette di visualizzare a video una shell (generalmente bash, ma può essere anche sh, zsh, chs, fish). È lei che gestisce i comandi e ci permette di eseguirli.

Va inoltre notato che linux, a differenza di windows, è case-sensitive, cioè differenzia le maiuscole con le minuscole. Quindi un file chiamato `testo` sarà diverso da un file chiamato `TeStO`.

Non vengono utilizzate le estensioni, perché il tipo di file viene definito all'interno di esso.

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

```bash
/home/giulio/documenti
```

Ma se ci si troverà già nella home, il percorso potrà essere espresso in modo relativo come:

```bash
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

### --recursive / -R

```bash
ls -R
```

Visualizza il contenuto delle sottodirectory in modo ricorsivo.

### --all / -a

```bash
ls -a
```

Visualizza anche i file nascosti.

### -l

```bash
ls -l
```

Visualizza informazioni aggiuntive riguardanti i file.

Con `--human`/`-h` le dimensioni saranno rappresentate con una scala adeguata e non in byte.

## pwd

Il comando `pwd` (acronimo di _print working directory_) visualizza la cartella in cui ci troviamo.

## cd

Il comando `cd` (acronimo di _change directory_) ci permette di cambiare la cartella in cui ci troviamo.

```bash
cd /home/giulio/documenti
```

Se non viene fornito un percorso utilizza la cartella home.

## mount

Il comando `mount` permette di montare un filesystem in una directory del sistema.

```bash
mount /dev/sda1 /mnt
```

È possibile specificare le directory di default nel file `/etc/fstab`, compreso se eseguire l'auto-mount.

# Lavorare con file e cartelle

## cp

Copia un file.

```bash
cp testo.txt copiaTesto.txt
```



## mv

Muove un file.

```bash
mv testo.txt nuovoTesto.txt
```



## rm

Rimuove permanentemente un file.

```bash
rm testo.txt
```



### --recursive / -r / -R

Viene utilizzato per rimuovere una directory.

```bash
rm -r cartella
```



## touch

Il comando `touch` permette di creare un file vuoto in una directory.

```bash
touch testo.txt
```

Come per ogni comando è possibile specificare un percorso assoluto:

```bash
touch /home/giulio/testo.txt
```



## mkdir

Il comando `mkdir` viene usato per creare una directory.

```bash
mkdir cartella
```

### --parents / -p

Con il parametro `-p` le cartelle superiori vengono create se non esistono.

Se per esempio vogliamo creare una cartella `/home/giulio/documenti/cartella`, ma la cartella `documenti` non esiste, è possibile crearla automaticamente con `-p`.

## chmod

Per cambiare i permessi di lettura, scrittura ed esecuzione di un file o cartella si può utilizzare il comando `chmod`.

**TODO: finire**

## chown

Ogni file o cartella ha un utente proprietario e un gruppo proprietario.

Per modificarli si utilizza il comando `chown`.

**TODO: finire**

# Gestione pacchetti

**TODO: finire**

## apt

## pacman

# Programmi utili

## dmesg

Visualizza i log del kernel.

## ip

Visualizza e modifica le proprietà delle interfacce di rete.

### address

Con il parametro `address` è possibile visualizzare gli indirizzi ip e MAC.

```bash
ip address
```

Questo parametro può essere abbreviato fino ad `a`.

```bash
ip a
```



## ssh

Permette di connettersi ad un server remoto via ssh.

```bash
ssh giulio@pc.local
```

Se il nome utente non viene specificato viene utilizzato quello dell'utente che esegue il comando.

### -p

È possibile specificare la porta del server con il parametro `-p`.

```bash
ssh -p 2222 giulio@pc.local
```

La porta utilizzata normalmente è la 22.

## scp

`scp` permette di copiare file da un computer all'altro tramite il protocollo ssh.

La sintassi è identica a `cp`, il file remoto (sorgente o destinazione che sia) va preceduto da `utente@hostname:`.

Esempio di copia di un file locale a una macchina chiamata `server`:

```bash
scp file.txt giulio@server.local:file.txt
```

## clear

Pulisce l'output della console.

Può essere utilizzata la scorciatoia `Ctrl + l`.

## exit

Esce dalla sessione attuale.

Può essere utilizzata la scorciatoia `Ctrl + d`.

## su

Permette di cambiare utente attuale:

```bash
su franco
```

Se non viene specificato nessun utente viene utilizzato quello di root.

## sudo

Permette di eseguire un comando come utente root.

```bash
sudo cp file.txt testo.txt
```

## halt / poweroff / shutdown

Per spegnere il sistema si possono utilizzare molti comandi, alcuni dei quali:

- **halt**
- **poweroff**
- **shutdown now**

## free

Visualizza la memoria (RAM) libera.

Con `--human`/`-h` verrà utilizzata una scala adeguata.

## top

Visualizza una tabella che mostra le risorse del sistema e i processi in esecuzione.

Una versione più avanzata è `htop`.

## ps

Riporta i processi attuali.

Per vedere i processi nel sistema utilizzare i parametri `aux`.

## pstree

Riporta un albero dei processi.

## uptime

Riporta il tempo passato dall'accensione del sistema.

## fdisk

Utility per visualizzare i dettagli delle partizioni ed eventualmente formattarle, crearle ed eliminarle.

## lsblk

Mostra i dispositivi di archiviazione connessi e le rispettive partizioni.

## id

Visualizza l'id dell'utente e dei gruppi a cui appartiene.

```bash
id giulio
```



## nano

Editor di testo molto semplice.

# TODO

**TODO: finire**

```
raspi-config
lscpu

cat
gcc
```

