---
layout: post
title: Cateva reguli pentru a scrie cod frumos in limbajul C
---

Din [regulile de programare in limbajul C de pe Algopedia](http://algopedia.ro/wiki/index.php/Reguli_ale_cercului_de_informatic%C4%83#Reguli_de_programare_.C3.AEn_limbajul_C), am gasit acestea fiind foarte importante.

### Indentarea

Codul trebuie sa fie indentat frumos (aliniat), ca sa poata fi citit de oricine. 

Cateva reguli de indentare:

#### Pentru fiecare nivel intr-un bloc de cod, codul trebuie indentat cu inca o unitate

Denumim o unitate caracterul sau caracterele care sunt inserate cand apesi pe Tab in Code::Blocks. Implicit, o unitate corespunde cu 4 spatii. Eu recomand 2 spatii, ca sa nu migreze prea mult codul spre partea dreapta a monitorului. Chiar daca majoritatea monitoarelor care se vand in ziua de azi sunt destul de late, cu raportul dintre latime si lungime fiind 16:9 sau chiar 16:10 la unele, daca codul migreaza prea la dreapta, o sa fie obositor sa iti plimbi ochii din stanga in dreapta monitorului.

Exemplu:

```c
#include <stdio.h>

int v[100]; // Suntem in nivelul 0; nu suntem in nici un bloc de cod
            // De aceea, indentam cu 0 unitati (0 unitati * 2 spatii = 0 spatii)

int main() {
  printf("Hello World!"); // Suntem in nivelul 1. (1 unitate * 2 spatii = 2 spatii)

  while (1) {
    printf("Ciclu infiniiiit!\n"); // Un bloc while in interiorul blocului functiei main => nivelul 2 => 2 * 2 = 4 spatii.

    for (i = 0; i < 3; i++) {
      printf("%d\n", i); // Nivelul 3 => 3 * 2 = 6 spatii
    }
  } 

  return 0;
}
```

**IMPORTANT: NU SE INDENTEAZA CU TAB**

De ce? Pentru ca lungimea unui caracter tab depinde de editorul de texte pe care il folosim.

#### Acolada deschisa se pune pe acelasi rand cu instructiunea precedenta

De ce? Pentru ca economisim spatiu pe verticala. Cum am zis mai sus, raportul dintre latime si lungime al monitoarelor din comert este 16:9 => verticala e foarte mica in comparatie cu latimea.

Exemplu:

```c
// Corect:
if (maDoareCeva()) {
  mergLaDoctor();
  sperCaMaVindec();
}

//Gresit:
if(maDoareCeva())
{
  maRog();
}

// Corect:
void mergLaDoctor() {
  ...
}

// Gresit:
void maRog() 
{
  ...
}
```

Nu zic ca nu e bine sa te rogi, dar e doar un exemplu.

#### Acolada inchisa se pune pe randul urmator aliniata sub instructiunea de care apartine

```c
// Corect:
if (maDoareCeva()) {
  mergLaDoctor();
  sperCaMaVindec();
}

// Gresit:
if(maDoareCeva())
{
  maRog();
  }

// Si mai gresit:
if(maDoareCeva())
{
  maRog();}
```

#### Dacă după else urmează un `if` atunci `if`-ul se pune imediat după `else` pe aceeași linie

Din nou, economisim spatiu pe verticala.

Exemplu:

```c
// Corect:
if (maDoareCeva()) {
  mergLaDoctor();
} else if (maDoareCapul()) {
  iauUnNurofen();
} else {
  ...
}

// Gresit:
if (maDoareCeva()) {
  mergLaDoctor();
} 
else if (maDoareCapul()) {
  iauUnNurofen();
} 
else {
  ...
}

// Mai gresit:
if (maDoareCeva()) {
  mergLaDoctor();
} 
if (maDoareCapul()) {
  iauUnNurofen();
} 
else {
  ...
}
```

#### Variabilele trebuie sa aiba nume clare

Nu cred ca e nevoie de exemplu.

### Lucrul cu fisiere in C

```c
FILE *fin, *fout; // Am declarat doua fisiere, fin si fout. Steluta e obligatorie

fin = fopen("in.txt", "r"); // fin reprezinta fisierul in.txt, deschis pentru citire
fout = fopen("out.txt", "w"); // fout reprezinta fisierul out.txt, deschis pentru scriere

fscanf(fin, "%d", &n); // Citim din fin un numar intreg "n". Obligatoriu &
fprintf(fout, "%d", n - 1); // Afisam la fout n - 1

// INCHIDEREA FISIERELOR - FOARTE IMPORTANTA
// Cand inchizi un fisier, se salveaza modificarile care nu s-au salvat si se inchid, facandu-se disponibile altor programe.
fclose(fin);
fclose(fout);
```

## Tema: un program simplu care foloseste toate lucrurile invatate din aceasta lectie. PANA JOI, 8 octombrie 2015