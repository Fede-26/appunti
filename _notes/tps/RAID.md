# Definizione
RAID significa (Redundant Array of Inexpensive Disks / Redundant Array of Indipendent Disks).

L'idea dietro al RAID è quella di utilizzare più dischi, facendo in modo che il sistema ne veda solo uno. Questo permette di aumentare la velocità di scrittura/lettura o di poter ripristinare tutti i dati nel caso di qualche guasto.


# Tipologie di RAID
Esistono diversi livelli di RAID, ognuno con diverse caratteristiche.

## RAID 0
Il RAID di livello 0 esegue uno _striping_ (scrittura/lettura su diversi dischi in modo continuo).
Non essendoci nessuna rindondanza, a volte non viene considerato un vero e proprio RAID.

![](../../assets/img/tps/raid0-20210102180007.png)

## RAID 1
Il RAID di livello 1 esegue una duplicazione di tutti i dati su ulteriori dischi.
Essendo che la scrittura deve essere doppia, non si ha un vantaggio; mentre nella lettura il carico può essere distribuito tra le due copie.

![](../../assets/img/tps/raid1-20210102180236.png)

## RAID 2
Il RAID di livello 2 esegue una duplicazione di tutti i dati su ulteriori dischi.
Essendo che la scrittura deve essere doppia, non si ha un vantaggio; mentre nella lettura il carico può essere distribuito tra le due copie.

![](../../assets/img/tps/raid2-20210102180539.png)