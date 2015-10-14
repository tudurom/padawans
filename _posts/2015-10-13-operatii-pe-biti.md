---
layout: post
title: Operatii pe biti
---

Deoarece calculatoarele "gandesc" folosing siruri de biti, programatorul trebuie
sa stie sa ii manipuleze.

## Ce este un *bit*?

Un bit este o cifra egala cu 0 sau cu 1.

Procesoarele calculatoarelor stocheaza toate numerele pe care opereaza (totul este un numar in procesor)
in baza 2, folosind impulsuri electrice. 0 inseamna ca nu trece curent, 1 inseamna ca trece curent.

De aceea, calculatoarele opereaza pe cifre binare; este cel mai usor mod.

V-ati putea intreba "dar ele pot sa opereze si pe numere reale si cu caractere!".

Nu tocmai.

Numerele reale sunt si ele *aproximate* in numere binare. De aceea nu poti sa exprimi o fractie zecimala periodica.

Caracterele sunt codificate prin [codul ASCII](https://ro.wikipedia.org/wiki/ASCII) sau [Unicode](https://ro.wikipedia.org/wiki/Unicode)(care include codul ASCII).

Atunci cand calculatorul ii spune monitorului ce sa afiseze, el defapt ii trimite o secventa de biti care ii spun ce pixeli sa aprinda.

## Operatii pe biti

### Operatorul `not`

In C se noteaza cu `~`.

El inverseaza bitii unui numar. Exemplu:

Reprezentarea in baza 2 a lui 5 este `00000101`. Inversand bitii =>
`~5 = -6 = 11111010 (binar)`.

### Operatorul `and` (`&`)

Definitie:

1 & 0 = 0
1 & 1 = 1
0 & 0 = 0
0 & 1 = 0

Adica: daca cei doi biti sunt 1, atunci returneaza 1.

Exemplu:

24 in binar -> `011000`
63 in binar -> `111111`
24 & 63 -> -> `011000` = 24

### Operatorul `or` (`|`)

Definitie:

1 | 0 = 1
1 | 1 = 1
0 | 0 = 0
0 | 1 = 1

Adica: daca unul dintre biti este 1, returneaza 1.

Exemplu:

420 in binar -> `110100100`
137 in binar -> `010001001`
420 | 137 -> `110101101` = 429

### Operatorul `xor` (`^`)

Adica *exclusive or* sau *sau exclusiv*.

Definitite:

1 ^ 0 = 1
1 ^ 1 = 0
0 ^ 0 = 0
0 ^ 1 = 1

Adica: returneaza 1 daca si numai daca un singur bit este egal cu 1.

Exemplu:

90 in binar -> `1011010`
42 in binar -> `0101010`
90 ^ 42     -> `1110000`

### Operatorul shift left (`<<`)

Primeste 2 numere (a si b). Muta fiecare bit din numarul `a` cu `b` pozitii spre stanga.

Exemplu:

12 -> `01100`
12 << 1 -> `11000`

**Observatie**: `a << b` = a * 2<sup>b</sup>.

### Operatorul shift right (`>>`)

Primeste 2 numere (a si b). Muta fiecare bit din numarul `a` cu `b` pozitii spre dreapta.

Exemplu:

12 -> `01100`
12 >> 1 -> `00110`

**Observatie**: `a >> b` = a / 2<sup>b</sup>.
Deoarece operatiile pe biti sunt mai rapide de cat impartirile (intotdeauna), pentru impartiriile la puteriile lui 2 este recomandat operatorul shift right, deoarece este mai rapid.

## Lectura
[Lectia depre operatii pe biti de pe Algopedia](http://algopedia.ro/wiki/index.php/Clasele_11-12_lec%C8%9Bia_6_-_22_oct_2014#Opera.C8.9Bii_pe_bi.C8.9Bi).

Este de la clasele 11-12. Nu va speriati :smile:!

# Tema

* Scrieti un program (in C) care citeste de la tastatura un numar `n` si afiseza la consola reprezentarea lui `n` in baza 2, folosind operatii pe biti.
* Problema [laborator de pe VianuArena](http://varena.ro/problema/laborator). Incercati sa o rezolvati folosind cat mai multe operatii pe biti.