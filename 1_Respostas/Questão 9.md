1. Escreva uma função em C que faz o debounce de botões ligados à porta P1.
```C
int Debounce (int BUTT){
Saida=P1IN & BUTT;
FOR(I=0;I<=6000;I++){
IF(P1OUT != Saida){     // Se houver variação na entrada, resetar a contagem
i=0;
}
}
RETURN (Saida)
}
```

2. Escreva um código em C que lê 9 botões multiplexados por 6 pinos, e pisca os LEDs da placa Launchpad de acordo com os botões. Por exemplo, se o primeiro botão é pressionado, os LEDs piscam uma vez; se o segundo botão é pressionado, os LEDs piscam duas vezes; e assim por diante. Se mais de um botão é pressionado, os LEDs não piscam.

```C
#DEFINE Y (BIT0|BIT1|BIT2) 
#DEFINE X (BIT3|BIT4|BIT5)
#DEFINE LEDS (BIT7|BIT6)
INT POSIÇÃO (VOID){
int Linha, coluna, botoes=0, i,j;
//DETERMINAR LINHAS

P1DIR|= ~Y;
P1DIR|= X;
P1REN |= Y;
P1OUT |=Y;
IF(((P1IN & BIT0) == 0)&&((P1IN & BIT1) == BIT1)&&((P1IN & BIT2) == BIT2)){
LINHA=1
}
ELSE IF(((P1IN & BIT0) == BIT0)&&((P1IN & BIT1) == 0)&&((P1IN & BIT2) == BIT2)){
LINHA=2
}
ELSE IF(((P1IN & BIT0) == BIT0)&&((P1IN & BIT1) == BIT1)&&((P1IN & BIT2) == 0)){
LINHA=3
}

//Determinar as colunas

P1DIR |= ~X;     
P1DIR |= Y;
P1REN &= ~Y
P1REN |= X;
P1OUT &= ~Y;
P1OUT |=X;
IF(((P1IN & BIT3) == 0)&&((P1IN & BIT4) == BIT4)&&((P1IN & BIT5) == BIT5)){
COLUNA = 1;
}
ELSE IF(((P1IN & BIT3) == BIT3)&&((P1IN & BIT4) == 0)&&((P1IN & BIT5) == BIT5)){
COLUNA = 2;
}
ELSE IF(((P1IN & BIT3) == BIT3)&&((P1IN & BIT4) == BIT4)&&((P1IN & BIT5) == 0)){
COLUNA = 3;
}
}
//nenhum botão apertado
IF((LINHA == 0) &&(COLUNA = 00){
P1OUT = ~(LEDS);
}
//algum botão apertado
ELSE(){
FOR(i=0;i<3;i++){
FOR(j=0;j<3,j++){
botao++;
if((linha==i)&& (coluna ==J)){
break;
}
}
}
}
return botão;
}
VOID Piscar (INT n_blinks){
P1OUT = 0;
P1DIR |= LEDS;
int i=0;
for(i=0;i<=n_blinks;i++){
P1OUT ^= LEDS; // PISCAR OS LEDS
P1OUT ^= LEDS;
}
RETURN;
}
INT MAIN (VOID){
WDTCTL = WDTPW | WDTHOLD;

PISCAR(POSIÇÃO());
}
```
