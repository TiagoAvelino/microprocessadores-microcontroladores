1- Barramento de endereços apenas apontam para o local da memomoria, já os barramentos de dados trabalham com os dados do projeto

2- A memoria RAM é uma memoria volatil e quando a energia acaba ela não mantem os dados armazenados, já a memoria ROM por ser não volatil mantem os dados armazenados, porem sua escrita é mais lenta quando comparada com a RAM.

3(a)- RAM, por que o valor dela não precisa estar fixo na memoria, por não se tratar do resultado requerido no programa.
 
 (b)- ROM, por que o resultado proveniente do programa devera ser armazenado mesmo com o desligamento da maquina.  
4- A arquitetura Havard  permite a leitura simultanea dos dados e do programa, permite barramento de dados e programa separadamente otimizados e ainda guarda dados constantes na memoria do programa, requerendo instrumentação especifica. Já a arquitetura Von Neumann é mais simples que a arquitetura Havard, sendo também menos eficiente.

5(a)- No local de memoria 0x0200, o valor recebido é DCBA e no local de memoria 0x201 o valor recebido é 1508
 
 (b)- No local de memoria 0x0200, o valor recebido é ABCD e no local de memoria 0x201 o valor recebido é 8051

6- Para somar duas variaveis de 32 bits é necessario primeiramente desmembrar cada numero de 32 bits em 2 numeros de 16 bits sendo que o primeiro numero no lugar da memoria é considerado o algarismo menos significativo, e o segundo o algarismo mais significativo, dessa forma é somado os algarismos menos significativos, verificando o acresimo de carry, armazendo esse valor em um outro registrador, e somar os algarismos mais significativos e regristar-los em outro local da memoria
