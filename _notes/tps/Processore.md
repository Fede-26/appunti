---
title: Processore
tags: Tps,Registri,CPU
toc: true
season: winter
---

# I registri
I registri si dividono in general purpose o special purpose.

## General purpose
Sono:

- `EAX`;
- `EBX`;
- `ECX`;
- `EDX`;
- `ESI` (source index);
- `EDI` (destination index).

![registri-20210102121903](../../assets/img/tps/registri-20210102121903.png)

## Special purpose
I registri special purpose si dividono in registri di segmento e altri

### Registri di segmento
Sono:

- `ECS` (code segment);
- `EDS` (data segment);
- `ES`  (extra segment);
- `SS`  (stack segment): indirizzo del segmento e offset top dello stack.

### Altri
Sono:

- `EIP`/`PC` (instruction pointer/program counter): contiene l'indirizzo della prossima istruzione che il processore deve eseguire;
- `ESP` (stack pointer);
- `EBP` (base pointer);
- `IR` (instruction register);
- `MAR` (memory address register);
- `MDR` (memory data register);
- ...


# Le cache
Le cache sono memorie molto veloci e si dividono in 3 livelli.
Le cache si possono inoltre distinguere se sono uniche o sono divise per dati e istruzioni.

Solo la cache L1 è fisicamente nel processore.

# Altri componenti
Sono:

- `MMU` (memory management unit): si occupa di gestire la memoria;
- `BUI` (bus unit interface): gestisce il bus;
- `ALU` (arithmetic and logic unit): si occupa di eseguire operazioni aritmetiche;
- `FPU` (floating point unit): esegue operazioni con i numeri a virgola mobile;
- `DU` (decoding unit): decodifica le istruzioni (tipo aritmetico, spostamento di valori, ...);
- `EU` (execution unit): esegue le istruzioni.

# Modalità di operazione
Un processore ha due modalità distinte per eseguire le operazioni:

- Modalità kernel ([Il kernel](Sistemi%20operativi#Il%20kernel));
- Modalità User.

Se l’istruzione viene eseguita se un processore in modalità kernel, essa può eseguire qualunque cosa senza nessun limite.
Se il processore si trova in modalità user, alcune operazioni dell’insieme di istruzioni non sono eseguibili perché non è autorizzato a farlo.

Nel registro `PSW` (registro dei flag) c’è un bit che indica in quale modalità il microprocessore è in esecuzione.

Un processo per passare dalla modalità User alla modalità Kernel deve eseguire una chiamata al sistema operativo. Questa istruzione viene chiamata `system call` o `TRAP`.