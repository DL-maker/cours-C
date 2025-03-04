
**1. Introduction et Opérateur Ternaire**

- Le point d'interrogation `?` est utilisé comme un opérateur ternaire pour exprimer une condition.
    - Exemple : `age = (est_majeur ? 18 : 17)`
    - Si `est_majeur` est vrai, `age` prend la valeur 18, sinon 17.

**2. Architecture CPU et RAM**

Extrait de code

```
flowchart LR
CPU --> RAM
```

![[image.webp]]

**3. Table ASCII**

| char | hex | dec | chor | ect | oct |
| :--- | :-- | :-- | :--- | :-: | :-: | | | | | | | |

- Différence entre 'A' et 'a' :
    - 32ème bit : A = 01000001 (65), a = 01100001 (97).
    - La différence de 32 en décimal se traduit par une différence d'un bit dans la représentation binaire.

**4. Représentation Hexadécimale**

- Conversion facile de l'hexadécimal au décimal :
    - FF (hex) = 255 (décimal) = 11111111 (binaire).
    - FF + 1 = 100 (hex).
    - 8 bits = 2 caractères hexadécimaux.

**5. UTF-8**

- Exemple : 'é' (e accentué)
    - Décimal : 233.
    - Hexadécimal : C3 A9.
    - Binaire : 11000011 10101001.
    - Les bits de début (110) indiquent que l'octet suivant fait partie du même caractère.

|110- - - - - - - -|1110 _ _ _ _|etc...|
|:--|:--|:--|
|2 octets|3 octets|etc...|

Exporter vers Sheets

**6. Terminal et Retours à la Ligne**

- Le terminal est un émulateur qui communique avec le noyau (kernel).
- Retours à la ligne :
    - MacOS : LF (Line Feed).
    - Windows : CRLF (Carriage Return Line Feed).
    - Linux : CR (Carriage Return).
- Caractère de fin : `/x00`.

**7. Architecture CPU et Instructions**

- Le nombre d'instructions dépend de l'architecture du CPU :
    - RISC (Reduced Instruction Set Computer) : moins de contrôle.
    - CISC (Complex Instruction Set Computer) : plus de contrôle.
- Nombres 64 bits :
    - Entiers non signés : 0 à 1844674407370...
    - Entiers signés : 1 bit de signe, 63 bits de valeur (complément à deux).
    - Virgule flottante : 1 bits de signe, 52 bits de mantisse, 11 bits d'exposant.
- Exemple d'addition (4 + 5) :

|0\ 4|1\ 5|2|3|
|:--|:--|:--|:--|
|4\||||
|8\ 1 => add||||
|12\|||15|

Exporter vers Sheets

- **Registres :**
    - IP (Instruction Pointer) : adresse de la prochaine instruction.
    - R1, R2, R3 : registres de données.
    - FLAGS : indicateurs d'état (ex : Overflow).


Instructions :
ADD | 1 | r1 = r1 + r2
POP | 2 | arg 1 id registre
Registre :
address de le premier instruction:
IP 8 => (Intruction Pointer)
R1 : 4
R2 : 8
R3 : 
FLAGS :
	- Overflow

Instructions 2 :
ADD | 1 | r1 = r1 + r2
Registre :
address de le premier instruction:
IP = 8 
R1 : 9
R2 : 8
R3 : 
FLAGS :
	- Overflow

Instructions 3 :
ADD | 1 | r1 = r1 + r2
Registre :
address de le premier instruction:
IP = 9
R1 : 9
R2 : 8
R3 : 
FLAGS :
	- Overflow
**8. RAM : Stack et Heap**

- **Stack (pile) :**
    - Croît vers les adresses basses.
    - Durée de vie courte (variables locales, appels de fonctions).
- **Heap (tas) :**
    - Croît vers les adresses hautes.
    - Durée de vie longue (allocation dynamique de mémoire).
    - brk : limite entre la mémoire allouée et non allouée du tas.
- Exemple : Fonction de Fibonacci (fib(n))

![[Pasted image 20250303141927.png]] ![[Pasted image 20250303142207.png]] ![[Pasted image 20250303142335.png]] ![[Pasted image 20250303142856.png]] ![[Pasted image 20250303142947.png]] ![[Pasted image 20250303143050.png]] ![[Pasted image 20250303143156.png]]
Instructions :
ADD | 1 | r1 = r1 + r2
POP | 2 | arg 1 id registre
Registre :
address de le premier instruction:
IP : 8
R1 : 26
R2 : 
R3 : 
FLAGS :
	- Overflow

Instructions 2 :
ADD | 1 | r1 = r1 + r2
POP | 2 | arg 1 id registre
Registre :
address de le premier instruction:
IP : 9
R1 : 27
R2 : 4
R3 : 
FLAGS :
	- Overflow3
	- 

Instructions 3 :
ADD | 1 | r1 = r1 + r2
POP | 2 | arg 1 id registre
Registre :
address de le premier instruction:
IP : 11
R1 : 27
R2 : 4
R3 : 5
FLAGS :
	- Overflow

Instructions 4 :
ADD | 1 | r1 = r1 + r2
POP | 2 | arg 1 id registre
Registre :
address de le premier instruction:
IP : 12
R1 : 28
R2 : 9
R3 : 5
FLAGS :
	- Overflow

![[Pasted image 20250303144533.png]]

**9. Appels Système (Syscalls)**

- Pour interagir avec le noyau (kernel).

|Commande/Registre|R1 (numero syscall)|R2|R3|R4|
|:--|:--|:--|:--|:--|
|EXIT|1|Code d'erreur (0: OK, 1: KO)|X|X|
|WRITE|2|1: stdout, 2: stderr|Adresse de la 1ère lettre|Nombre de caractères|


- MMU (Memory Management Unit) : wikipedia MMU.

nstructions :
ADD | 1 | r1 = r1 + r2
POP | 2 | arg 1 id registre
SYSCALL | 3 | X
MOV | 4 | Valeur Immediate & Registre
PUSH | 5 | agr 1 : id registre
MOVRR | 6  | src => dst

Registre :
address de le premier instruction:
IP : 13
SP : 28
R1 : 9
R2 : 5
R3 : ...
R4  : 
FLAGS :
	- Overflow

** Note 0x30 : `0`
	9 + 0x30 : `9`

info : immediate = une valeur qui se trouve dans le code

Instructions 2 :
ADD | 1 | r1 = r1 + r2
POP | 2 | arg 1 id registre
SYSCALL | 3 | X
MOV | 4 | Valeur Immediate & Registre
PUSH | 5 | agr 1 : id registre
MOVRR | 6  | src => dst

Registre :
address de le premier instruction:
IP : 13
SP : 28
R1 : 9
R2 : 5
R3 : ...
FLAGS :
	- Overflow



**10. Instructions et Registres**

- Instructions :
    - ADD, POP, SYSCALL, MOV, PUSH, MOVRR.
- Registres :
    - IP, SP (Stack Pointer), R1, R2, R3, R4, FLAGS.
- Exemple : Conversion de 9 en caractère ASCII ('9') : 9 + 0x30 = '9'.
- immediate : valeur directement dans le code.

![[Pasted image 20250303152404.png]]
Instructions 3 :
ADD | 1 | r1 = r1 + r2
POP | 2 | arg 1 id registre
SYSCALL | 3 | X
MOV | 4 | Valeur Immediate & Registre
PUSH | 5 | agr 1 : id registre
MOVRR | 6  | src => dst

Registre :
address de le premier instruction:
IP : 17
SP 32
R1 : 32
R2 : 9
R3 : 5
FLAGS :
	- Overflow

Instructions 4 :
ADD | 1 | r1 = r1 + r2
POP | 2 | arg 1 id registre
SYSCALL | 3 | X
MOV | 4 | Valeur Immediate & Registre
PUSH | 5 | agr 1 : id registre
MOVRR | 6  | src => dst

Registre :
address de le premier instruction:
IP : 19
SP : 32
R1 : 0x39
R2 : 0x30
R3 : ...
FLAGS :
	- Overflow


![[Pasted image 20250303152945.png]]
nstructions 5 :
ADD | 1 | r1 = r1 + r2
POP | 2 | arg 1 id registre
SYSCALL | 3 | X
MOV | 4 | Valeur Immediate & Registre
PUSH | 5 | agr 1 : id registre
MOVRR | 6  | src => dst

Registre :
address de le premier instruction:
IP : 19
SP : 31
R1 : 0x39
R2 : 0x30
R3 : ...
R4 : ...
FLAGS :
	- Overflow

Instructions 6 :
ADD | 1 | r1 = r1 + r2
POP | 2 | arg 1 id registre
SYSCALL | 3 | X
MOV | 4 | Valeur Immediate & Registre
PUSH | 5 | agr 1 : id registre
MOVRR | 6  | src => dst

Registre :
address de le premier instruction:
IP : 25
SP : 31
R1 : 2
R2 : 1
R3 : ...
R4 : 1
FLAGS :
	- Overflow

Instructions 7 :
ADD | 1 | r1 = r1 + r2
POP | 2 | arg 1 id registre
SYSCALL | 3 | X
MOV | 4 | Valeur Immediate & Registre
PUSH | 5 | agr 1 : id registre
MOVRR | 6  | src => dst

Registre :
address de le premier instruction:
IP : 31
SP : 31
R1 : 2
R2 : 1
R3 : 31
R4 : 1
FLAGS :
	- Overflow
___


**11. Gestion de la Stack (Pile)**

- Pour agrandir la pile, réduire le pointeur de pile (rsp).
    - exemple: sub rbp
- Registres : rbp (Base Pointer), rsp (Stack Pointer).
- Prologue :
    - `mov rsp, rbp`
    - `sub rsp, 3`
- Épilogue :
    - `leave` (équivalent à `mov rsp, rbp; pop rbp`)
    - `ret` (équivalent à `pop rip`).
- `call` : enregistre l'adresse de retour sur la pile.
- wikipedia call convention.

![[Pasted image 20250303161941.png]]

**12. Labels**

- Labels globaux (ex : fib) pour le disque.
- Labels locaux (ex : fib_loop) pour le code.

![[Pasted image 20250303164353.png]] ![[Pasted image 20250303164922.png]] ![[Pasted image 20250303165034.png]] ![[Pasted image 20250303165524.png]]

---
La mémoire et les langages de programmation : une vue d'ensemble

Au cœur du système, les octets (8 bits) forment la RAM, organisée en stack (appels de fonctions), heap (données dynamiques) et text (code). La notation hexadécimale facilite la lecture des octets.

Au-dessus, les adresses mémoire, données (floats, chars) et instructions sont gérées par l'MMU, qui traduit les adresses virtuelles en adresses physiques.

L'assembleur (ASM) permet un contrôle direct de ces éléments, mais est complexe. Le C, plus abstrait, offre un équilibre entre performance et facilité d'utilisation.

Les langages de haut niveau comme Python et les frameworks comme Django simplifient le développement d'applications complexes.

Les MMaps (Memory Maps) sont utilisés pour mapper des fichiers en mémoire, optimisant les performances.

En résumé, cette hiérarchie représente les différents niveaux d'abstraction entre le matériel et les applications, permettant aux développeurs de choisir le niveau approprié.

![[Pasted image 20250304095010.png]]
Creer un program assembleur:
```asm
/fib 10
sys argv = ["fib", "10"]

=> La ram nous attribue des addresse de memoire
[134,130]
```
![[Pasted image 20250304100418.png]]
** TRES PROBABLE QUE CELA CE RETROUVE DANS LE STACK
Apres que le Kernel la seulemnt construit MAINTENAT JE DOIS A accessder
![[Pasted image 20250304101106.png]]
** agrc = Nombre de argument 
   argv = Liste de arguement 

```C
main(int argc, char**argv)
```
int au debut indique la type envoyer par le programme
=> argv = 138 => or address ...

return 0; => Mettre 
![[Pasted image 20250304103530.png]]
```asm
mov rdi, 0
mov rax, 60
syscall
** Note => exit(0) = return 0
```

`char **argv` => c'est un caractere
`char ** argv` => c'est un Pionter vers un caractere
`char ** argv` => C'est l'addresse de l'address d'un caracter

** Note pour debeug et appel systeme du programme : strace
   Affichage en hexa les truc qu'il a recu : hexadump

On va creer essay de creer un write() a la bonne taille de ...  la chaine de caractere
Pour cela on scanne la RAM, sachant qu'il connait le premier caractere jusqu'a qu'il trouve 0 pour trouver la taille de la chaine de caractere.

Si le first_char = 0 en retourne la taille de la chaine: o'u *first_char c'est un caractrer. 
Sinon en ragoute + 1 a la variable len et on fait first_char = first_char + 1 => Pour avancer dans la ram
![[Pasted image 20250304120138.png]]
```C
int write(int, char*, int);
int read(int,char*,int);
int exit(int);

int string_size(char *first_char){
        int len 0;
        while (1){
                if (*first_char == 0){
                        return len;
                }
                else{
                        len = len + 1;
                        first_char = first_char + 1;
                }
        }
}

int main(int argc, char** argv[]){
        write(1,*argv, string_size(*argv) );
        exit(0);
};
```

PYTHON VS C:
Le passage de paramettre SONT TOTALEMENT DIFFERENT

int write(int, char*, int);
int read(int,char*,int);
int exit(int);
** Note des PROTOTYPE DE FONCTION

---
man 1 => Shell
man 2 => syscall 
man 3 => fonction stdi => stand out & stand int

exemple :
man 1 exit => Pour voir les prototype => <stdlib.h> (exit)
man 3 write => Pour voir les prototype => <unistd.h> (read, write, ...)

`# include fait un copier coller dans de les fonction`

Sauvegarde a un pointer :
```
pushq %rbp
```

de placer les donners d'un pointer a un autre pointer : :
```asm
movq %rdi,  %rxa
```

...
```
movsql ... , ...
```


ELF => FORMA EXECUTABLE SUR LINUX

Pour afficher le HEX + ASSEMBLEUR
```
objdump -Mintel -d nomfufichier
```

![[Pasted image 20250304145450.png]]
erreur stgsegv => Indique que le code a essayer de lire dans une partie la ram qui est n'est pas autoriser

** Rappel : Pour tranformer le chaine de caractere en chiffre => 
```
'8' - '0'= 8
0x38 - 0x30 = 8
```
Pour reparer ce probleme => On mets comme condition dans main avant de executer le string_stat() c'st if argc >= 2 pour check elle n'est pas aussi grande dans le dossie dans le stop
# A NE PAS OUBLIER 0 = 0x30

```C
int write(int, char*, int);
int read(int,char*,int);
int exit(int);

int string_size(char *first_char){
        int len 0;
        while (1){
                if (*first_char == 0){
                        return len;
                }
                else{
                        len = len + 1;
                        first_char = first_char + 1;
                }
        }
}

int fib(int n) {
    if (n < 2) {
        return 1;
    }
    return fib(n-1) + fib(n-2);
}

void print_int(int values){
        int last_digit = value%10;
        int remaining_digits = values / 10;
        char last_digit as a char = last_digit + 0x30;
        if (remaining_digits){
                print_int(remaining_digits)
        }
        write(1, &last_digit as a char, 1);
        print_int(remaining_digits); 
}

int main(int argc, char** argv[]){
        if (argc >=2){
                char n_as_a_char = **(argv + 1);
                int n = n_as_a_char - 0x30;
                int result = fib(n);
                print_int(result);
                //write(1,*(argv+1), string_size(*(argv+1) ));
                char new_line = 0x0A;
                write(1, &new_line, 1);
        }
        exit(0);
        
        
};

```
