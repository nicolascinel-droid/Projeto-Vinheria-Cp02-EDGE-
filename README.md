# Projeto-Vinheria-Cp02-EDGE-
Sistema de monitoramento ambiental inteligente para controle de temperatura, umidade e luminosidade em vinherias utilizando Arduino.


🌡️ SISTEMA INTELIGENTE DE MONITORAMENTO AMBIENTAL PARA A VINHERIA COM ARDUNIO 

📖 DESCRIÇÃO DO PROJETO

Este projeto tem como objetivo desenvolver um sistema automatizado de monitoramento ambiental para armazenamento de vinhos utilizando a plataforma Arduino.

O sistema realiza monitoramento em tempo real de:

🌡️ Temperatura
💧 Umidade
☀️ Luminosidade
🕒 Horário em tempo real

Além disso, o projeto possui:

Sistema de alertas visuais e sonoros;
Display LCD I2C;
RTC DS1307;
EEPROM;
Navegação por botão;
Calibração automática de luminosidade.

Esse tipo de automação é fundamental para preservar:

sabor;
aroma;
qualidade;
durabilidade dos vinhos.

O projeto demonstra a aplicação prática da automação e dos sistemas embarcados no controle ambiental inteligente.

🚀 FUNCIONALIDADES

✅ Monitoramento de temperatura em tempo real
✅ Monitoramento de umidade
✅ Monitoramento de luminosidade
✅ Sistema de alertas automáticos
✅ Controle visual com LEDs
✅ Alertas sonoros com buzzer
✅ Interface LCD I2C
✅ RTC com horário em tempo real
✅ Navegação entre telas via botão
✅ Armazenamento de dados na EEPROM
✅ Calibração automática do sensor LDR
✅ Comunicação serial para depuração

🧰 COMPONENTES UTILIZADOS
Componente	Função
Arduino Uno	Microcontrolador principal
DHT22	Sensor de temperatura e umidade
LCD I2C 16x2	Interface visual
RTC DS1307	Relógio em tempo real
Sensor LDR	Monitoramento de luminosidade
LEDs	Indicadores de status
Buzzer	Alertas sonoros
Botão Push Button	Navegação entre telas
EEPROM	Armazenamento persistente
Protoboard	Montagem do circuito
Jumpers	Conexões

🧠 FUNCIONAMENTO DO SISTEMA

O sistema realiza leituras contínuas dos sensores conectados ao Arduino.

As informações coletadas são processadas em tempo real e exibidas no display LCD.

Com base nos valores monitorados:

LEDs indicam o estado do ambiente;
O buzzer emite alertas;
Dados são armazenados na EEPROM;
O usuário pode alternar as telas utilizando um botão.
🌡️ CONTROLE DE TEMPERATURA

O sistema monitora constantemente a temperatura ambiente.

📌 Faixas Utilizadas
Temperatura	Status
10°C ~ 18°C	Ideal
> 18°C	Alerta
> 25°C	Crítico
< 5°C	Crítico
💧 CONTROLE DE UMIDADE
Umidade	Status
60% ~ 80%	Ideal
Fora da faixa	Alerta
< 40% ou > 90%	Crítico
☀️ CONTROLE DE LUMINOSIDADE

O sistema utiliza um sensor LDR para monitorar a intensidade luminosa do ambiente.

A luminosidade é calibrada automaticamente para melhorar a precisão da leitura.

🚨 SISTEMA DE ALERTAS

O projeto possui três estados principais:

Estado	LED	Buzzer
Normal	Verde	Desligado
Alerta	Amarelo	Bip curto
Crítico	Vermelho	Bip longo
🖥️ INTERFACE LCD

O display LCD exibe:

Temperatura;
Umidade;
Luminosidade;
Horário atual.

As telas podem ser alteradas através do botão físico conectado ao Arduino.

🕒 RTC DS1307

O módulo RTC é responsável por manter:

data;
horário;
sincronização do sistema.

Mesmo com o Arduino desligado, o RTC continua funcionando através de bateria própria.

💾 EEPROM

O sistema utiliza EEPROM para salvar dados importantes do monitoramento.

Os valores armazenados incluem:

Temperatura;
Umidade;
Luminosidade.
🔌 ESQUEMA DO CIRCUITO
🌐 Simulação Wokwi

https://wokwi.com/projects/464557863911736321?utm_source=chatgpt.com

💻 CÓDIGO DO PROJETO
📚 Bibliotecas Utilizadas
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
#include <DHT.h>
#include <RTClib.h>
#include <EEPROM.h>

🖥️ Inicialização do LCD
LiquidCrystal_I2C lcd(0x27, 16, 2);
🌡️ Inicialização do DHT22
#define DHTPIN 6
#define DHTTYPE DHT22
DHT dht(DHTPIN, DHTTYPE);

🕒 RTC
RTC_DS1307 rtc;

🔌 Definição dos LEDs
const int ledVerde = 2;
const int ledAmarelo = 3;
const int ledVermelho = 4;
🔊 Buzzer
const int buzzer = 5;

☀️ Sensor LDR
const int ldrPin = A0;
🎛️ Botão de Navegação
const int botao = 8;

📥 Leitura dos Sensores
float temperatura = dht.readTemperature();

float umidade = dht.readHumidity();

int ldrValor = analogRead(ldrPin);

🔄 Conversão da Luminosidade
int luminosidade = map(ldrValor, ldrMin, ldrMax, 0, 100);
🚨 Controle de Alertas
if (critico) {

  digitalWrite(ledVermelho, HIGH);

  tone(buzzer, 1000);

  delay(400);

  noTone(buzzer);
}

💾 EEPROM
EEPROM.write(0, (int)t);
EEPROM.write(1, (int)u);
EEPROM.write(2, (int)l);

🔄 FLUXOGRAMA DO SISTEMA
Inicialização
      ↓
Leitura dos Sensores
      ↓
Processamento dos Dados
      ↓
Verificação dos Alertas
      ↓
Atualização do LCD
      ↓
Armazenamento EEPROM
      ↓
Loop Contínuo 

📂 ESTRUTURA DO PROJETO
📦 Projeto-Vinheria-Cp02-EDGE
 ┣ 📜 codigo.ino
 ┣ 📜 README.md
 ┣ 📂 imagens
 ┣ 📜 diagram.json
 ┗ 📜 wokwi-link.txt
 
🛠️ COMO EXECUTAR
Monte o circuito conforme o diagrama;
Abra o código na IDE do Arduino;
Conecte o Arduino ao computador;
Selecione a placa Arduino UNO;
Faça o upload do código;
Execute a simulação ou circuito físico;
Acompanhe os dados pelo LCD e monitor serial.
🧪 APLICAÇÕES

Este projeto pode ser utilizado em:

🍷 Vinherias
🌱 Agricultura
🏠 Automação residencial
🧪 Laboratórios
🏭 Monitoramento industrial
🌡️ Controle ambiental
📡 Projetos IoT

🚀 MELHORIAS FUTURAS
Integração com ESP32;
Dashboard Web;
Wi-Fi;
MQTT;
Aplicativo mobile;
Banco de dados;
Monitoramento remoto;
Cartão SD;
Gráficos em tempo real.

👨‍💻 AUTORES
Nícolas Cinel
Luis Fernando
Kelvin Lucas
Gabriel
Leonardo Formigari
🎓 Curso

Edge Computing & Computer Systems

👨‍🏫 Professor

Fabio Cabrini

📌 OBSERVAÇÕES

Projeto desenvolvido para fins acadêmicos utilizando Arduino, automação e conceitos de sistemas embarcados.
