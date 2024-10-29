# Ponderada Semáforo

## Parte 1 Código utilizado

´´´ C++
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

const int greenpin = 8;
const int yellowpin = 4;
const int redpin = 12;
const int buzpin = 10;
LiquidCrystal_I2C lcd(0x27, 16, 2); 

void setup() {
  pinMode(redpin, OUTPUT);
  pinMode(greenpin, OUTPUT);
  pinMode(yellowpin, OUTPUT);
  pinMode(buzpin, OUTPUT);
  lcd.init();    
  lcd.print("carregando...");
  lcd.backlight();    
  lcd.setCursor(0, 1);     
  lcd.print("");     
}

void ligarled(int cor, int tempo, bool isred, String aviso) {

  lcd.clear();
    if (isred) {
    tone(buzpin, 3000);
  } else {
    noTone(buzpin); 
  }


  lcd.print(aviso);
  digitalWrite(cor, HIGH);  
  delay(tempo * 1000); 
  digitalWrite(cor, LOW); 
}

void loop() {
  ligarled(redpin, 6, true,"PARE");
  ligarled(yellowpin, 2, false,"CORRA");
  ligarled(greenpin, 4, false, "PODE IR");
  ligarled(yellowpin, 2, false, "CORRA");
}

´´´

&nbsp;&nbsp;&nbsp;&nbsp; No código a cima, o que eu fiz foi eu basicamente busquei fazer o código o mais otimizado possível e para isso eu utilizei de funções e parâmetros apra conseguir isso. Comecei importando as bibliotecas necessárias para utilizar o painel lcd, depois eu comecei por definir as variáveis de entrada dos pinos dos leds e buzzers, depois utilizei o setup para indicar qual é o pinMode dos pinos e a inicialização do lcd. Depois disso, começa a parte mais importante do código a função. Na função, eu exigo os parâmetros: cor, tempo, um booleano se é vermelho ou não e uma string com a mensagem que vai aparecer no painel. Com esses dados, eu toco o buzzer se o booleano for verdadeiro, printo a imagem do aviso, e acendo o led correto (definido pelo pino da variavel cor) pelo tempo definido e, por fim, eu apago o led e reseto a mensagem do painel. Por fim, eu começo um loop que basicamente indica a ordem dos leds seguido pelos parâmetros da função. 

## Parte 2: Imagens
&nbsp;&nbsp;&nbsp;&nbsp; Segue as imagens do circuito.
<div align="center">
<sub>Figura 1 — Semaforo <a href="#c6"></a></sub> </br>
<img src="assets\semaforo.jpg"><br>
</div><br>

<div align="center">
<sub>Figura 2 — Painel lcd <a href="#c6"></a></sub> </br>
<img src="assets\painellcd.jpg"><br>
</div><br><div align="center">

<sub>Figura 3 — Circuito visto de cima <a href="#c6"></a></sub> </br>
<img src="assets\circuitocima.jpg"><br>
</div><br>

### Parte 3: Vídeo

https://github.com/user-attachments/assets/83e54866-3ca1-42ea-b221-47e95059a60c


### Parte 4: Materias utilizados

| Material                       | Quantidade |
|--------------------------------|------------|
| LED vermelho                   | 1          |
| LED verde                      | 1          |
| LED amarelo                    | 1          |
| Arduino                        | 1          |
| Jumper macho-fêmea             | 10         |
| Jumper macho-macho             | 6          |
| Painel LCD                     | 1          |
| Buzzer                         | 1          |
| Resistores 330Ω                | 3          |
| Recorte de madeira de um semáforo | 1      |


### Parte 5: Ir além
&nbsp;&nbsp;&nbsp;&nbsp; Para ir além, o que eu fiz foi utilizar um buzzer que apitasse sempre que a cor do semáforo estivesse em vermelho, a fim de avisar os pedestres a toimar cuidado. Além disso, eu fui além ao adicionar um painel lcd que mostrasse mensagens de aviso dependendo da cor que estivesse o semaforo, sendo elas: verde: pode ir, amarelo: corre e vermelho: cuidado.
### Parte 6: Avaliação Pares

### Avaliador: Marcelo Conde Filho

| Critério                                                                                                 | Contempla (Pontos) | Contempla Parcialmente (Pontos) | Não Contempla (Pontos) | Observações do Avaliador |
|---------------------------------------------------------------------------------------------------------|--------------------|----------------------------------|--------------------------|---------------------------|
| Montagem física com cores corretas, boa disposição dos fios e uso adequado de resistores                | Até 3              | Até 1,5                            | 0                        |  Em geral o setup esta bom, porém inicialmente bagunçado, mas da pra perceber que eles estao seguindo a ordem das leds. Então, por exemplo os fios vermelhos estão seguindo a led vermelha.                         |
| Temporização adequada conforme tempos medidos com auxílio de algum instrumento externo                  | Até 3              | Até 1,5                          | 0                        |   O tempo está correto e após a contação manual está correto.                        |
| Código implementa corretamente as fases do semáforo e estrutura do código (variáveis representativas e comentários) | Até 3              | Até 1,5                          | 0                        |   O código foi extremamente bem implementado com o uso de funções sendo extremamente optimizado                        |
| Extra: Implmeentou um componente de liga/desliga no semáforo e/ou usou ponteiros no código | Até 1              |  Até 0,5                         | 0                        |  O felipe utilizou o lcd para falar se a pessoa deve correr, parar, ou ir, e um buzzer que ativa com a led vermelha.                          |
|  |                                                             |  |9.7 |**Pontuação Total**|
