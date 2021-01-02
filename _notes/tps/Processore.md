---
title: Processore
tags: Registri,CPU
toc: true
season: winter
---

# I registri
I registri si dividono in general purpose o special purpose.

## General purpose
Sono:

- `EAX`
- `EBX`
- `ECX`
- `EDX`
- `ESI` (source index)
- `EDI` (destination index)

![registri-20210102121903](../../assets/img/tps/registri-20210102121903.png)

## Special purpose
I registri special purpose si dividono in registri di segmento e altri

### Registri di segmento
Sono:

- `ECS` (code segment)
- `EDS` (data segment)
- `ES`  (extra segment)
- `SS`  (stack segment, indirizzo del segmento e offset top dello stack)

### Altri
Sono:

- `EIP`/`PC` (instruction pointer, rappresenta la prossima istruzione)
- `ESP` (stack pointer)
- `EBP` (base pointer)
- ...