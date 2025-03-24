
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

---
![[Pasted image 20250317111424.png]]
Pour voir la RAM libre (sur Linux), il faut écrire free -h → le -h est pour que ce soit lisible pour un humain Chaque octet dans la RAM à son adresse, les registres n’ont pas d’addrese à t on le droit d’écrire partout dans la RAM ? 
En théorie oui mais en pratique non Pourquoi l’inplémentation de fib qu’on a fait est si lente ? 
Pour faire fib(6), il doit faire fib(5) + fib(4), pour faire fib(5) = fib(4) + fib(3), etc…

![[Pasted image 20250317111634.png]]
![[Pasted image 20250317111946.png]]
```ASM
global main
add:
	push rbp ;prologue
	mov rbp, rsp ;prologue
	add rdi, rsi ; -> rdi = rdi + rsi
	mov rax, rdi
	pop rbp ;epilogue
	ret ;epilogue
main:
	push rbp
	mov rbp, rsp
	mov rdi, 11 ;1er argument
	mov rsi, 12 ;2eme argument
	call add
	mov rax, 0 ;return 0 donc si le programme réussi
	pop rbp
	ret
```

On veut le compiler
`nasm -g -f elf64 add.s -o add.o`
fichier nasm
`-g → pour avoir des symboles de debug`

à la fin, cela nous fait un fichier .o qui n’est pas un programme

gcc -g3 add.o -o add pour avoir le fichier en executable add est l’executable

sans mov rax, 0 , quand on execute le programme, il crache et nous donne le nombre directement alors qu’avant on le voyait pas

x/20i → explore 20 instructions à partir de cette adresse

si → step instruction

(gdb) → debugger d’Assembleur et de C

Du gros au petit bout (de l’oeuf) → Big endian - gros boutiste Du petit au gros bout → Little endian - petit boutiste

![[Pasted image 20250317113216.png]]

outil a installer = 
sudo apt install nasm
sudo apt install gdb

```
nasm -g -f elf64 add.s -o add.o
Maintenant le faire avec trois valeur
Traduction en C
gcc add.o -o add
	gdb add
b main
r
exit
./add
echo $?
```

```C
int add(int a, int b) {
return a + b;
}
void main(void) {
add(4, 8);
}

int main (void) { 
	char un = '1'; 
	char deux = '2'; 
	char *hello1 = "Hello world\n";
	char *hello2 = "Hola!\n";
	print_string(hello1);
	print_string(hello2);
}

void print_string(char *address_of_first_char) {
while(1){
	if (*address_of_first_char == 0)
	return;
	write(1, //sortie = stout
	address_of_first_char, // addresse du premier caractère à afficher
	1); //nombre de caractère à afficher
	address_of_first_char += 1;
	}
}
```

---
Aujourd’hui on va créer des nouveaux types
`struct` pour créer un nouveau type
```C 
struct point {
	int x;
	int y;
}; // Ce code crée la structure x et y et les met côte à côte
```

`typedef` permet de renommer un type
```C
int main (void) {
	int toto;
	struct point p1;
	
	p1.x = 10;
	p1.y = 11;
	
	return 0;
}
```

Le but de `malloc` est de gérer la heap
```ASM
Dump of assembleur code for function main:
0x000... <+0>   push   %rbp
0x000... <+1>   mov    %rsp, %rbp
0x000... <+4>   movl   $0xa, -0x8(%rbp)
0x000... <+11>  movl   $0xb, -0x4(%rbp)
0x000... <+18>  mov    $0x0, %eax
0x000... <+23>  pop    %rbp
0x000... <+24>  ret
End of assembleur dump
```
![[Pasted image 20250317113747.png]]

On veut que le fonctionne aggrandise la partie utilise de la stack pour ce code(?)

```C
int write(int, char *, int); //pour savoir dans quel registre il faut ele mettre 

int main (void) {
	int toto;
	struct point p1;
	
	p1.x = 10;
	p1.y = 11;
	
	write(1, "hello\n", 6);
	
	return 0;
}
```

```ASM
Dump of assembleur code for function main:
0x000... <+0>   push   %rbp
0x000... <+1>   mov    %rsp, %rbp
0x000... <+4>   sub    $0x10, %rsp # Cette ligne montre que la taille est 
									agradit pour pouvoir mettre rsp dans la 
									stack
								-> int toto et struct point p1
```

![[Pasted image 20250317113902.png]]
![[Pasted image 20250317114701.png]]
Le code attribue à `toto` 4 octets et à `point` 8 octets, car puisque `point` sait qu'il est seul, il veut organiser à sa guise.

```bash
hexdump -C fichier.png
```

![[Pasted image 20250317115432.png]]
```
sudo apt install strace
strace file file.pdf
```
![[Pasted image 20250317120834.png]]
Les pallettte sert a attribuer des couleur en HEX

wiki Profondeur de C 

```C
struct png { // Coder un decodeur de PNG

int data_ength;

int chunk_name;

int width;

int height;

unsigned char bit_depth;

unsigned char color_type;

unsigned char compression;

unsigned char filter;

unsigned char interleaving;

}
```

Mais le problème est que le code doit fonctionner même lorsque le PDF a une architecture de 4 octets de décalage. Cela fonctionne sur l'ordinateur du professeur, mais cela ne marchera pas nécessairement chez les autres.

```C
struct png { // Coder un decodeur de PNG

int data_ength;

int chunk_name;

int width;

int height;

unsigned char bit_depth;

unsigned char color_type;

unsigned char compression;

unsigned char filter;

unsigned char interleaving;

}

  

int main (void) {

unsigned char png_data[29];

// File Descriptor (Numero du fichier)

int fd = open("test.png", O_RDONLY);

if (fd == -1){

printf("Can't open test.png\n");

return 1;

}

read(fd, png_data, 29);

return 0;

}
```

## /!\ Pourquoi png data.width et png_data.height valent autant ????????????? /!\
Quand on affiche les octets => 
```
(gdb) x/4x &png_data.height
0x574658465873658736 : 0x00 0x00 0x01 0x5e 
```
LE VRAI PROBLEME C'EST QUE LA STRUCTURE EST ON little indiane donc il fait le lire de manier inverse

```C
#include <endian.h>
#include <stdlib.h>
#include <math.h>
#include <stdio.h>
#include <unistd.h>
#include <stdint.h>
#include <fcntl.h>

struct png {
    uint64_t sig;
    uint32_t data_length;
    uint32_t chunk_name;
    uint32_t width;
    uint32_t height;
    unsigned char bit_depth;
    unsigned char color_type;
    unsigned char compression;
    unsigned char filter;
    unsigned char interleaving;
};

struct point {
    long x;
    long y;
};

double point_dist_from_point(struct point self, struct point other) {
    return sqrt(
        pow(self.x - other.x, 2) +
        pow(self.y - other.y, 2)
    );
}

double point_dist_from_origin(struct point self) {
    struct point origin;

    origin.x = 0;
    origin.y = 0;

    return point_dist_from_point(self, origin);
}

void point_print(struct point self) {
    printf("Point(x=%ld, y=%ld)\n", self.x, self.y);
}

int main(void) {
    struct png png_data;
    // File Descriptor (numéro du fichier)
    int fd = open("test.png", O_RDONLY);

    if (fd == -1) {
        printf("Can't open test.png\n");
        return EXIT_FAILURE;
    }

    read(fd, &png_data, sizeof(png_data));

    png_data.height = be32toh(png_data.height);
    png_data.width = be32toh(png_data.width);

    printf("%s: %d×%d\n", "test.png", png_data.width, png_data.height);
    return EXIT_SUCCESS;
}
```
Dans la bibliotheque `#include <stdint.h>` il y a  le unint{bits}

___
---

On va aujourd'huis en va voir les outil autour de C
```C
#include <fcntl.h>

int main(void){
char data[1024];
int fd = open("Hello.md", O_RDONLY);

close(fd);

return 0;
}
```
On peut utiliser des fichier avec des parametre tels que 
`char data[1024];` => Lire les 1024 caractere (octet) MEME SI LA VALEUR C 0 => mais on 
`O_RDONLY` => Open en Lecture => en le prefixe pour que on n'as pas espace de nommage en C donc on evite quelle soit et devient une source de ecrasement
`close(fd);` => Fermeture du fichier => Si on ne le close pas que ce passe t'il ? => Le kernel va libret l'espace et donc fermer le fichier MAIS quand le code meur.


---
```C
#include <fcntl.h>
#include <unistd.h>

int main(void){
char data[1024];
int fd = open("Hello.md", O_RDONLY);

ssize_t nb_bytes =  read(fd, data, 1024);

close(fd);

write(1, data, nb_bytes);

return 0;
}
```

`ssize_t nb_bytes =  read(fd, data, 1024);` =>
`write(1, data, nb_bytes);` => 

---
Comment ecrire un caractere nul dan sun fichier POUR voir que le  `read(fd, data, 1024)` qu'il puisse lire ou non un caractere null

```C
#include <fcntl.h>
#include <unistd.h>

int main(void){
if (argc < 2) {
	printf("Please give me a filename as arguement \n);
	retirn EXIT_FAILURE;
}

char data[1024];
int fd = open(argv+1, O_RDONLY); // ou ARGV+1

ssize_t nb_bytes =  read(fd, data, 1024);

close(fd);

write(1, data, nb_bytes);

return 0;
}
```
![[Pasted image 20250318103058.png]]

** Note : `argv[1] = * (argv + 1) = *(1 + argv)`

---
dans le <stdlib.h> il y a comme fonctionnaliter `int getc(FILE *stream);`
=> Car si getc  prends en compte un octet 

---
`strace` pour voir tout les appel system
exemple :
```bash
strace ./a.out
```
option 
-o  => Mettre un aout put sur un fichier 
-s =>  Pour afficher les hex cacher par defaut
-f => Si le programme invoque un autre programme ce programme va etre s trace

---
`readelf` Pour afficher les en-tete d'un fichier info :
`readelf -h` 
```bash
...txt...
Adresse du point d'entree : 0x10a0 => On peut seulemnt dire que le pointe d'entre en relatif et non exacte car quand on execute le programme le kernel le meme de manier "Random"
...txt...
```

-a => pour tout afficher
On a trouver :
```bash
(Requisition de l'interpreteur de programme: /lib64/ld-linux-x86-64.so.2)
```
C'est quoi ld => c'est un linqueur qui est l’adresse de la RAM
Il va même le code de printf dans le ld
** Note => A approfondie
___
Si on continue a faire un programme qui est donner la même mémoire les fonction dans la RAM
il peut etre exploitet (exemple BufferFlow)
___

`gdb` => Debeugeur
```bash
b  main
```
sert a mettre des pints d'arret
```
r [(variable si besion pour le code)]
```
executer le code 
```
n
```
Pour passer au prochain points d'arret
```
p [un variable]
```
pour afficher les variables ou sont placer dans la RAM
```
x/[NOMBRE DE D'instruction] (avec c pour caractere ou b pour bite ou a pour adresse )
```
EXEMPLE 
```bash
(gdb) x/3a argv 0x7fffffffdd68: 0x7fffffffe0fa 0x7fffffffe117                      0x7fffffffdd78: 0x0 
(gdb) x/10c 0x7fffffffe0fa 0x7fffffffe0fa: 47 '/' 104 'h' 111 'o' 109 'm' 101 'e' 47 '/' 109 'm' 100 'd' 
0x7fffffffe102: 107 'k' 47 '/' 
(gdb) x/10c 0x7fffffffe117 
0x7fffffffe117: 104 'h' 101 'e' 108 'l' 108 'l' 111 'o' 46 '.' 109 'm' 100 'd' 
0x7fffffffe11f: 0 '\000' 80 'P'
```

BONUS il y a une version graphique de gdb `gdb -tui`
        autre extention comme `gef` bien presenter MAIS il faut se abituer

---
`objdump` => ...
-d => deassembler
-Mintel => Pour les processus INTEL
-D => Deasemble tout ce qui n'est pas du code aussi exemple (des commentaire)

___
`nm` => ...
exemple de commande :
`nm hello`
`nm -D /usr/lib/x86_64-linux-gnu/libc.so.6`

___
valgrind => Pour voir que la gestion du code dans la memoire  
EXEMPLE 
```bash
ld@LD:~$ valgrind ls
==7250== Memcheck, a memory error detector
==7250== Copyright (C) 2002-2022, and GNU GPL'd, by Julian Seward et al.
==7250== Using Valgrind-3.19.0 and LibVEX; rerun with -h for copyright info
==7250== Command: ls
==7250== 
add    add.s	Documents  Music     Public	Videos
add.o  Desktop	Downloads  Pictures  Templates
==7250== 
==7250== HEAP SUMMARY:
==7250==     in use at exit: 23,939 bytes in 18 blocks
==7250==   total heap usage: 55 allocs, 37 frees, 63,422 bytes allocated
==7250== 
==7250== LEAK SUMMARY:
==7250==    definitely lost: 0 bytes in 0 blocks
==7250==    indirectly lost: 0 bytes in 0 blocks
==7250==      possibly lost: 0 bytes in 0 blocks
==7250==    still reachable: 23,939 bytes in 18 blocks
==7250==         suppressed: 0 bytes in 0 blocks
==7250== Rerun with --leak-check=full to see details of leaked memory
==7250== 
==7250== For lists of detected and suppressed errors, rerun with: -s
==7250== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)

```
___
makefile => faire des raccoucie
EXEMPLE DE CONTENUE DE MAKEFILE
```
hello.o: hello.c
	cc $(CFLAGS) -c hello.c -o hello.o

hello: hello.o
	cc hello.o -o hello

.PHONY: clean
clean:
	rm -f hello hello.o
```

___
![[Pasted image 20250318142741.png]]

BRK => 

** Note : perror => Affiche l'erreur 
```C
#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>

char *read_file(char *filename){
    void *base_brk = sbrk(1000);
    int fd = open(filename, O_RDONLY);
    if (fd==-1){
        return NULL;
    }
    ssize_t byte_read = read(fd, base_brk, 999);
    close(fd);
    *(base_brk + byte_read) = '/0'; 
    return base_brk
}


int main(int argc, char *argv[]) {
    // argv[0] == "read file" le nom du programme
    // argv[1] : son premier parametre
    // argv[2] : son 2eme parametre
    // ...
    if (argc < 2){
        printf("Donner une valeur...");
        return EXIT_FAILURE;
    }

    char * file_contents = read_file(argv[1]);
    if (file_contents) {
        print_file_contents(file_contents);
    }
    return EXIT_SUCCESS;
}
```

le `file_contents` => l'adresse va vers la stack et l'autre va en la heap





