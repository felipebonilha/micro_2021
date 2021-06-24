# micro_2021_Lab_1

Alterando as intruções MOV por MVN no exercício 3, é possível observar que as operações passaram a inserir o valor negado nos registradores, como vemos abaixo passo a passo:

             MVN R0, #0x55 -> o valor negado de 55 é 0xffff'ffaa e este valor pode ser observado na janela registrador 1, onde R0 assume este valor
              
             MVN R1, R0, LSL #16 -> o valor 0xffff'ffaa é deslocado para a esquerda em 16 bits, em seguida inserido o seu valor negado no registrador R1
             portando 0xffff'ffaa deslocado -> 0xffaa'0000 e inserido o valor negado -> 0x0055'ffff
              
             MVN R2, R1, LSR #8 -> o valor 0x0055'ffff é deslocado para a direita em 8 bits, em seguida inserido o seu valor negado no registrador R2
             portando 00x0055'ffff deslocado -> 0x0000'55ff e inserido o valor negado -> 0xffff'aa00
              
             MVN R3, R2, ASR #4 -> o valor 0xffff'aa00 é deslocado de maneira aritmética para a direita em 4 bits, em seguida inserido seu valor negado no registrador R3
             portando 0xffff'aa00 deslocado -> 0xffff'faa0 e inserido o valor negado -> 0x0000'055f
             
             MVN R4, R3, ROR #2 -> é realizado a operação ROR #2 em 0x0000'055f, em seguida inserido o seu valor negado no registrador R4
             portando 0xffff'aa00 ROR #2 -> 0xc000'0157 e inserido o valor negado -> 0x3fff'fea8
             
             MVN R5, R4, RRX é realizado a operação RXX em 0x3fff'fea8, em seguida inserido o seu valor negado no registrador R5
             portanto 0x3fff'fea RRX, 0x1fff'ff54 e inserido o valor negado -> 0xe000'00ab
