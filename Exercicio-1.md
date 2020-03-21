# Exercício 1 - INF 351

Valéria Carneiro - 89397

Gabriel Teixeira - 78473

Luciana Tavares - 85270

Rafael Brum - 89366


# Pull-Up e Pull-Down

São técnicas utilizadas na montagem de chaves de circuito. Na técnica pull-up, a saida do circuito será alta quando o botão não estiver pressionado e baixa quando estiver pressionado, já no pull-down acontece justamente o contrário, veremos o porquê.

## Pull-up

Nessa técnica, a chave do circuito é ligada no pino (I/O) e no terra (GND) criando um caminho alternativo para a corrente. Na montagem inicial, como abaixo, o botão não está pressionado, portanto não passa corrente e o caminho de menor resistência é o do LED, que fica então aceso. Ao pressionar o botão, entretanto, o LED se apaga. Isso acontece pois o LED já não representa mais o caminho de menor resistência, a corrente passa então pelo botão.

![Pull up](https://github.com/luciana-t/Arduino-1o/blob/master/images/ex1_img1.png)


## Pull-down

A montagem do pull-down se difere no fato de a chave ser ligada em série com o circuito e portanto ao invés de criar um caminho alternativo para a corrente ela interrompe a corrente e portanto o LED inicialmente fica desligado, mas ao pressionar o botão a corrente pode fluir e o LED fica ligado.

![Pull down](https://github.com/luciana-t/Arduino-1o/blob/master/images/ex1_img2.png)


## Parte 1

"Chave pullup, 2 leds, cada vez que aperta acende um led e apaga o outro, alterna"

<a href="https://youtu.be/zgwSqW1qHWU"><img src="https://github.com/luciana-t/Arduino-1o/blob/master/images/ex1_vid1.png" 
alt="IMAGE ALT TEXT HERE" width="240" height="180" border="10" /></a>

[TINKERCAD LINK 1](https://www.tinkercad.com/things/elZh2S2EOET)

Segue o código usado para resolver a Parte 1 do Exercício 1 no TINKERCAD:

```C
void setup() {
  Serial.begin(9600);
  pinMode(2,INPUT_PULLUP); //botão pull up
  pinMode(5, OUTPUT); //led1
  pinMode(4, OUTPUT); //led2
}
int led1 = 5;
int led2 = 4;

void loop() {
  int sensorValue = digitalRead(2);
  Serial.println(sensorValue, DEC);
  
  if (sensorValue == LOW) {
    digitalWrite(led1, HIGH);
    digitalWrite(led2, LOW);
  } else {
    int aux = led1;
    led1 = led2;
    led2 = aux; 
  }
  delay(10); 
}
```

## Parte 2

"Chave pullup, 2 leds, solta led 1 piscando, apertada: led 1 acesso e led 2 piscando."

<a href="https://youtu.be/YYWKLdGqxfo"><img src="https://github.com/luciana-t/Arduino-1o/blob/master/images/ex1_vid2.png" 
alt="IMAGE ALT TEXT HERE" width="240" height="180" border="10" /></a>

[TINKERCAD LINK 2](https://www.tinkercad.com/things/lGywAGGgeAs)


Segue o código usado para resolver a Parte 2 do Exercício 1 no TINKERCAD:

```C
void setup() {
  Serial.begin(9600);
  pinMode(2,INPUT_PULLUP); //botão pull up
  pinMode(5, OUTPUT); //led1
  pinMode(4, OUTPUT); //led2
}

int led1 = 5;
int led2 = 4;

void loop() {
  int sensorValue = digitalRead(2);
  Serial.println(sensorValue, DEC);
  
  if (sensorValue == LOW) {
    digitalWrite(led1, HIGH);
    digitalWrite(led2, HIGH);
    delay(50);
    digitalWrite(led2, LOW);
    delay(50);
  } else {
    digitalWrite(led1, HIGH);
    delay(50);
    digitalWrite(led1, LOW);
    delay(50);
    digitalWrite(led2, LOW);
  }
  delay(10); 
}
```
