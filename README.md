# SensorDistanciaMQTT
Implementação de um sensor de distância com uma placa ESP32 e comunicação com Ubidots pelo protocolo MQTT

Para fazer esse projeto foram utilizados os seguintes componentes:
1 Placa ESP32
1 Sensor de distância Ultrassônico HC-SRO4
6 Jumpers Macho-Fêmea
1 Buzzer Ativo
1 Protoboard

Para montagem, olhar o arquivo PNG com a montagem do circuito;
Resumo das conexões:
VCC (Sensor) x VIN (ESP32) --Essa conexão é responsável pela passagem de energia para o Sensor (5V)
Trig (Sensor) x GPIO4/D4 (ESP32)
Echo (Sensor) x GPIO5/D5 (ESP32)
GND (Sensor) x GND (ESP32)
+/Maior conector/Esquerda (Buzzer) x GPIO21/D21 (ESP32)
Menor Conector/Direita (Buzzer) x GND (ESP32)

Utilizada a IDE Arduino
Abaixo segue um vídeo tutorial para configuração da IDE do Arduino para utilização do ESP32 feito pelo canal do Youtube FernandoKTecnologia:
https://www.youtube.com/watch?v=gLfVBOMJ2Nw

Para a utilização do protocolo MQTT foi utilizado o Broker Ubidots:
Necessária a criação de um usuário no link: https://ubidots.com/
O Ubidots também possui app para celular android e pode ser baixado de graça na play store.
Para a criação deste projeto, que tem como objetivos acadêmicos foi utilizada a licença free
No link abaixo há outro tutorial de como utilizar o Ubidots com a ESP32 feita pelo canal FernandoKTecnologia:
https://www.youtube.com/watch?v=D0CqWpeZ0yY

Um resumo das etapas:

1. Deve ser criado um usuário, depois deve-se consultar o perfil e verificar se há algum dado pendente (Importante, pois se o perfil não estiver completo, pode acarretar em problemas na criação de um dispositivo)
2. Depois de criado um usuário, deve-se criar um dispositivo - O nome escolhido para a criação do dispositivo será a label do tópico utilizado na conexão no código. ex.: #define TOPIC "/v1.6/devices/esp32-distancia", no caso esp32-distancia foi o nome escolhido para o meu dispositivo no ubidots.
3. Depois de criado o dispositivo, você terá acesso aos dados necessários para conexão. Cuidado, pois os dados são privados e garantem que outras pessoas não acessem seu dispositivo! Para sua segurança, mantenha-os em segredo. Esses dados estão com X no código .ino fornecido nesse github. Esses dados devem ser sobrescritos com os dados de sua conexão:
#define TOKEN "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" //Inserir Token pessoal do dispositivo Ubidots
#define DEVICE_ID "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" //Inserir Device ID UBIDOTS (Código exclusivo do usuário)
Além da criação do dispositivo, há duas alternativas: a criação da variável que contém os dados do sensor antes da conexão com o dispositivo ou não criar a variável e permitir que o próprio ubidots identifique e crie a variável dentro do seu dispositivo. Em todo caso, a variável será utilizada na implementação da conexão do MQTT:
#define VARIABLE_DISTANCIA "distancia" //Label referente a variável de distância criada no Ubidots

Neste momento, já é possível acessar o código .ino e substituir os campos com X ou dados genéricos pelos seus próprios dados. São eles: 
#define WIFISSID "seuSSID" //inserir SSID Wifi
#define PASSWORD "suaSenha" //Inserir Senha Wifi
#define TOKEN "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" //Inserir Token pessoal do dispositivo Ubidots
#define DEVICE_ID "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" //Inserir Device ID UBIDOTS (Código exclusivo do usuário)

Depois que esses dados forem inseridos, seu programa estará pronto para ser compilado e testado na placa.

Abaixo seguem mais tutoriais do canal FernandoKTecnologia do Youtube utilizados como referência para montagem da placa:
Sensor Ultrassônico parte 1:
https://www.youtube.com/watch?v=Rx3hkcfdL8Q
Sensor Ultrassônico parte 2:
https://www.youtube.com/watch?v=L3Q-4xUszoo

A codificação da conexão MQTT e captura de dados do sensor foram baseadas na demonstração apresentadas no vídeo, sendo adaptadas ao conceito deste projeto. 
https://youtu.be/xKUtb6IBPCU


