Para as questões 2 a 5, considere que as variáveis f, g, h, i e j são do tipo inteiro (16 bits na arquitetura do MSP430), e que o vetor A[] é do tipo inteiro. Estas variáveis estão armazenadas nos seguintes registradores: f: R4 g: R5 h: R6 i: R7 j: R8 A: R9 Utilize os registradores R11, R12, R13, R14 e R15 para armazenar valores temporários.

1-Escreva os trechos de código assembly do MSP430 para: 
(a) Somente setar o bit menos significativo de R5.

```C
bis.w BIT0,R5
```

(b) Somente setar dois bits de R6: o menos significativo e o segundo menos significativo. 

bis.w BIT0,R6
bis.w BIT1,R6

(c) Somente zerar o terceiro bit menos significativo de R7.

bic.w BIT2, R7

(d) Somente zerar o terceiro e o quarto bits menos significativo de R8.

bic.w BIT2,R8
bic.w BIT3,R8

(e) Somente inverter o bit mais significativo de R9.

inv.w BITF,R9

(f) Inverter o nibble mais significativo de R10, e setar o nibble menos significativo de R10.

inv.w F,R10
inv.w E,R10
inv.w D,R10
inv.w C,R10
bis.w BIT0,R10
bis.w BIT1,R10
bis.w BIT2,R10
bis.w BIT3,R10

2-"Traduza" o seguinte trecho de código em C para o assembly do MSP430:

if(i>j) f = g+h+10;
else f = g-h-10;
```C
mov.w R5, R11
mov.w #10,R12
mov.w R6,R13
Comp R7,R8 ;COMP=i>j
jl i_maior_que_j
sub.w  R11,R12
sub.w R12,R13
JUMP EXIT

i_maior_que_j:
add.w R6,R11
add.w R11,R12
mov.w R12,R4

EXIT:

```


3-"Traduza" o seguinte trecho de código em C para o assembly do MSP430:
while(save[i]!=k) i++;

```C
LOOP: mov.w R7, R12 
inc.w R12  
add.w R10, R1.w
cmp 0(R12), R9 
jnq EXIT  
inc.w R7 
jmp LOOP
EXIT:
...
```

4-"Traduza" o seguinte trecho de código em C para o assembly do MSP430:
for(i=0; i<100; i++) A[i] = i*2;
```C
mov.w #0, R7
LOOP: mov.w R7,R12
rla R12
mov.w R12,R9(R12)
cmp R12,#100
inc R7
jl loop
Exit:
...
```

5-"Traduza" o seguinte trecho de código em C para o assembly do MSP430:
for(i=99; i>=0; i--) A[i] = i*2;
```C
mov.w R7,R12
mov.w #99, R7
loop:
rla R12
mov.w R12,R12(R9)

cmp #0, R7
dec.w R7
jge loop
```


