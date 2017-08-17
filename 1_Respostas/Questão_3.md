1 Dada uma variável a do tipo char (um byte), escreva os trechos de código em C para: 
(a) Somente setar o bit menos significativo de a.

char a 
{ a |= BIT1;}

(b) Somente setar dois bits de a: o menos significativo e o segundo menos significativo.

{ a |= BIT0 | BIT1;}

(c) Somente zerar o terceiro bit menos significativo de a.

{ a &=~ BIT2;}

(d) Somente zerar o terceiro e o quarto bits menos significativo de a.

{ a &= BIT2 | BIT3;}

(e) Somente inverter o bit mais significativo de a.

{ a ^= BIT7;}

(f) Inverter o nibble mais significativo de a, e setar o nibble menos significativo de a. 

{ a ^= BIT7+BIT6+BIT5+BIT4
  a |= BIT0+BIT1+BIT2+BIT3
}

2 Considerando a placa Launchpad do MSP430, escreva o código em C para piscar os dois LEDs ininterruptamente.

#include <msp430g2553.h>
#define LED1 BIT0
#define LED2 BIT6
void main(void){
int i=0;
 WDTCTL = WDTPW | WDTHOLD;
 P1OUT = 0;
 P1DIR = LED1 + LED2;
 for(;;)
 {
 P1OUT ^= LED1 + LED2;
 for(i=0;i<=10;i++){
 }
}

3 Considerando a placa Launchpad do MSP430, escreva o código em C para piscar duas vezes os dois LEDs sempre que o usuário pressionar o botão.

//Ligar LEDS enquanto o
//botão estiver pressionado
#include <msp430g2553.h>
#define BTN BIT2
#define LED1 BIT0
#define LED2 BIT6
void main(void){
 WDTCTL = WDTPW | WDTHOLD;
 int i=0;
 P1OUT = 0;
 P1DIR = LED1 + LED2;
 for(;;)
 {
 while((P1IN & BTN) != 0){}
 for(i=0;i<=3;i++){
 P1OUT ^= LED1 + LED2;
 }
 while((P1IN & BTN) == 0){}
 P1OUT &= ~(LED1 + LED2);
 }
}

4 Considerando a placa Launchpad do MSP430, faça uma função em C que pisca os dois LEDs uma vez.
#include <msp430g2553.h>
#define BTN BIT2
#define LED1 BIT0
#define LED2 BIT6
void Piscar (void){
 int i=0, j=0;
 P1OUT = 0;
 P1DIR = LED1 + LED2;
 for(j=0;j<=1;j++)
 {
 P1OUT ^= LED1 + LED2;
 for(i=0;i<=10;i++){
 }
}

5 Reescreva o código da questão 2 usando a função da questão 4.

void main(void){
 WDTCTL = WDTPW | WDTHOLD;
 for(;;)
 {
Piscar();
}


6 Reescreva o código da questão 3 usando a função da questão 4.

void main(void){
 WDTCTL = WDTPW | WDTHOLD;
 for(;;){
 while((P1IN & BTN) != 0){}
 for(i=0;i<=1;i++){
Piscar();
while((P1IN & BTN) == 0){}
 P1OUT &= ~(LED1 + LED2);
}
