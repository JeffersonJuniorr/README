Nome dos integrantes do grupo:
Jefferson Junior Alvarez Urbina

Turma: (1ESPG)

Ano: 2024

Objetivo
Vocês foram contratados pela Vinheria Agnello para desenvolver um sistema de monitoramento a ser instalado no ambiente em que os vinhos são armazenados. O dono a Vinheria informou que a qualidade do vinho é influenciada diretamente pelas condições de temperatura, umidade e luminosidade do ambiente. Neste primeiro momento, você propôs ao dono da Vinheria um projeto em etapas, de modo que seu 1° desafio é:

Elaborar um sistema usando Arduino que faça a captura das informações de luminosidade do ambiente. Para isso pesquise sobre o LDR. Verifique como eles funcionam e como poderiam ser usados no projeto.

De posse dos dados coletados, implemente um sistema de alarme, utilizando LEDs, para sinalizar quando o a ambiente estiver OK, ou quando alguma grandeza estiver fora dos limites estipulados. Use um LED verde para indicar que está OK, um LED amarelo para indica que está em níveis de alerta e um LED Vermelho para indicar que tem algum problema.

Quando a luminosidade estiver em nível de alerta, deve soar uma buzina (buzzer) por 3 segundos. A buzina volta a soar caso a luminosidade permaneça em nível de alerta.

Descrição do desafio
Desenvolvimento do projeto
Enfrentamos alguns desafios durante o desenvolvimento, tais como a regulagem da luminosidade necessaria para soar o alarme e o led amarelo

Como executar o projeto
Para executar o projeto, é necessario fazer a montagem do circuito disponibilizado, tambem se da necessario uma regulagem do sensor LDR. (Indicação comentada no código)

Projeto
https://www.tinkercad.com/things/4BYyx9sU3Yo-vinheria-agnello-cp1

Codigo
const int buzzerPin = 7; // Alarme no pino 7
const int ldrPin = 0; // LDR no pino analógico 0

const int ledVerde = 8;
const int ledAmarelo = 9;
const int ledVermelho = 10;

int ldrValue = 0; // Valor lido do LDR
const int freq = 5; // altera frequencia do sonorizador

void setup() {
 //Ativando o serial monitor que exibirá os valores lidos no sensor.
 Serial.begin(9600);
 //Definindo pinos digitais dos leds e buzzer como de saída.
 pinMode(buzzerPin, OUTPUT);
 pinMode(ledVerde,OUTPUT);
 pinMode(ledAmarelo,OUTPUT);
 pinMode(ledVermelho,OUTPUT);
}

void loop() {
ldrValue = analogRead(ldrPin); // lê o valor do LDR

//Luminosidade Alta. (Esse valor poderá variar de acordo com o hambiente)
if (ldrValue > 950) {
 apagaLeds();
 digitalWrite(ledVermelho,HIGH);
 
 //Toca o alarme
 tone(buzzerPin,1000); // toca um tom de 1000 Hz
 delay(3000); // espera um pouco
 noTone(buzzerPin); // interrompe o tom
 delay(ldrValue); // espera a quantidade de milissegundos em ldrValue
}

//Luminosidade média. (Esse valor poderá variar de acordo com o hambiente)
if (ldrValue >= 200 && ldrValue <= 950) {
 apagaLeds();
 digitalWrite(ledAmarelo,HIGH);
}

//Luminosidade Baixa. (Esse valor poderá variar de acordo com o hambiente)
if (ldrValue < 200) {
 apagaLeds();
 digitalWrite(ledVerde,HIGH);
}

//Exibindo o valor do sensor no serial monitor.
Serial.println(ldrValue);

delay(50); 
}

//Função criada para apagar todos os leds de uma vez.
void apagaLeds() {
digitalWrite(ledVerde,LOW);
digitalWrite(ledAmarelo,LOW);
digitalWrite(ledVermelho,LOW);
} 


Componentes
- 1 Protoboard
- 13 Jumpers
- 2 Resistores de 100Ω
- 1 Ressitor de 15kΩ
- 1 Resistor 10kΩ
- 3 LEDs sendo (1 Vermelho, 1 Amarelo e 1 Verde)
- 1 Sensor de luminosidade LDR
- 1 Arduino
- 1 Pieza
