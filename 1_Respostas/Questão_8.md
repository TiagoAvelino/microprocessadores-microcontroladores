Para todas as questões, utilize os LEDs e/ou os botões da placa Launchpad do MSP430.

1-Escreva um código em C que pisca os LEDs ininterruptamente.
```C
#include <msp430g2553.h>
#define LED1 BIT0
#define LED2 BIT6
#define LEDS (LED1+LED2)
/*função atraso*/
void delay(volatile unsigned int i){
while(i<5000)
{
i++;
}
}

int main(void)
{
WDTCTL = WDTPW | WDTHOLD;
P1DIR |= LEDS; // setando saidas e entradas
P1OUT |= LEDS;
while(1){
PIOUT^= LEDS;
delay(0);
}
return 0;
```
2-Escreva um código em C que pisca os LEDs ininterruptamente. No ciclo que pisca os LEDs, o tempo que os LEDs ficam ligados deve ser duas vezes maior do que o tempo que eles ficam desligados.

```C
#include <msp430g2553.h>
#define LED1 BIT0
#define LED2 BIT6
#define LEDS (LED1+LED2)
void delay(volatile unsigned int i){
while(i<5000)
{
i++;
}
}

int main(void)
{
WDTCTL = WDTPW | WDTHOLD;
P1DIR |= LEDS; // setando saidas e entradas
P1OUT |= LEDS;
while(1){
PIOUT^= LEDS;
delay(0);
PIOUT^= LEDS;
delay(2500);
}
return 0;
```
3-Escreva um código em C que acende os LEDs quando o botão é pressionado.
```C
#include <msp430g2553.h>
#define BTN BIT2
#define LED1 BIT0
#define LED2 BIT6
void main(void){
WDTCTL = WDTPW | WDTHOLD;
P1OUT = 0;
P1DIR = LED1 + LED2;
for(;;)
{
if(P1IN & BTN == 0)
P1OUT |= LED1 + LED2;
else
P1OUT &= ~(LED1 + LED2);
}
}
```
4-Escreva um código em C que pisca os LEDs ininterruptamente somente se o botão for pressionado.

```C
#include <msp430g2553.h>
#define BTN BIT2
#define LED1 BIT0
#define LED2 BIT6
/*função atraso*/
void delay(volatile unsigned int i){
while(i<5000)
{
i++;
}
}
void main(void){
WDTCTL = WDTPW | WDTHOLD;
P1OUT = 0;
P1DIR = LED1 + LED2;
for(;;)
{
if(P1IN & BTN == 0)
while(1){
PIOUT^= LEDS;
delay(0);
}
else
P1OUT &= ~(LED1 + LED2);
}
}
```
5-Escreva um código em C que acende os LEDs quando o botão é pressionado. Deixe o MSP430 em modo de baixo consumo, e habilite a interrupção do botão.
