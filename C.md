
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