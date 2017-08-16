Dada uma variável a do tipo char (um byte), escreva os trechos de código em C para: 
(a) Somente setar o bit menos significativo de a.

char a 
{ a |= BIT1;}

(b) Somente setar dois bits de a: o menos significativo e o segundo menos significativo.

{ a |= BIT0 + BIT1;}

(c) Somente zerar o terceiro bit menos significativo de a.

{ a &=~ BIT2;}

(d) Somente zerar o terceiro e o quarto bits menos significativo de a.

{ a &= BIT2 + BIT3;}

(e) Somente inverter o bit mais significativo de a.

{ a ^= BIT7;}

(f) Inverter o nibble mais significativo de a, e setar o nibble menos significativo de a. 

{ a ^= BIT7+BIT6+BIT5+BIT4
  a |= BIT0+BIT1+BIT2+BIT3
}

Considerando a placa Launchpad do MSP430, escreva o código em C para piscar os dois LEDs ininterruptamente.

Considerando a placa Launchpad do MSP430, escreva o código em C para piscar duas vezes os dois LEDs sempre que o usuário pressionar o botão.

Considerando a placa Launchpad do MSP430, faça uma função em C que pisca os dois LEDs uma vez.

Reescreva o código da questão 2 usando a função da questão 4.

Reescreva o código da questão 3 usando a função da questão 4.
