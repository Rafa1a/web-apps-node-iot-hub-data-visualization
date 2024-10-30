# Documentação do Projeto: Visualização de Dados do Azure IoT Hub
 
Este documento fornece um roteiro de prática para configurar e executar um aplicativo web para visualização de dados provenientes do Azure IoT Hub. Siga os passos abaixo para configurar seu ambiente de desenvolvimento e implantar o aplicativo na nuvem Azure.

Link: https://webfullstackiot.azurewebsites.net/

Link Será retirado, logo após a correção do Projeto.

Video do projeto em execução: 

![ProjetoFacu](/imagens/Gravando%202024-03-11%20201112%20(1).gif)

## Pré-requisitos

- Conta no Microsoft Azure.
- Navegador Web (Google Chrome, Firefox, MS Edge, Safari ou Opera).
- Visual Studio Code (VS Code).
- Raspberry Pi Azure IoT Online Simulator.[Raspberry Pi Azure IoT Online Simulator](https://azure-samples.github.io/raspberry-pi-web-simulator/#GetStarted)

## Procedimentos

- Antes Precisa criar hub IOT no azure 
- Adicionar um dispositivo 
- Usar o Raspberry Pi para enviar Dados ao seu dispositivo criado
  
### 1. Baixar e Configurar o Código-fonte

- Acesse o repositório do aplicativo web no GitHub: [Azure Samples - Web Apps Node IoT Hub Data Visualization](https://github.com/Azure-Samples/web-apps-node-iot-hub-data-visualization).
- Clone ou faça o download do código-fonte.
- Descompacte os arquivos em uma pasta de sua escolha.
- Abra a pasta do aplicativo Web em sua IDE preferida, como o Visual Studio Code.

### 3. Adicionar Grupo de Consumidores ao Hub IoT

- Execute o seguinte comando na CLI do Azure para adicionar um grupo de consumidores ao ponto de extremidade interno do hub IoT:
az iot hub consumer-group create --hub-name YOUR_IOT_HUB_NAME --name YOUR_CONSUMER_GROUP_NAME

Execução: 

![grupo de consumidores](/imagens/grupo%20de%20consumidores.png)


### 4. Configurar Variáveis de Ambiente

- Obtenha a cadeia de conexão do serviço para seu hub IoT com o seguinte comando:
  
az iot hub show-connection-string --hub-name YOUR_IOT_HUB_NAME --policy-name service

Execução: 

![connectionString](/imagens/connectionString.png)

Utilize os comandos abaixo na janela de comando para definir as variáveis de ambiente:

set IotHubConnectionString=YOUR_IOT_HUB_CONNECTION_STRING

set EventHubConsumerGroup=YOUR_CONSUMER_GROUP_NAME

PowerShell : 

$env:IotHubConnectionString = "YOUR_IOT_HUB_CONNECTION_STRING"

$env:EventHubConsumerGroup = "YOUR_CONSUMER_GROUP_NAME"

![connectionString](/imagens/variaveis%20de%20ambiente.png)

### 5. Executar o Aplicativo Web Localmente

- Execute os seguintes comandos no terminal para baixar e instalar os pacotes e iniciar o site:
  
npm install
npm start

### 6. Visualizar Dados Localmente

- Abra uma página da web acessando http://localhost:3000 em seu navegador.
- Escolha o dispositivo desejado na lista para visualizar um gráfico em tempo real dos últimos 50 pontos de dados de temperatura e umidade.
  
inicio:

![exceção do projeto localmente](/imagens/execucao.png)

localhost: 

![exceção do projeto localmente grafico](/imagens/execucao_grafico.png)

Console:

![exceção do projeto localmente console](/imagens/execucao_console.png)

### 7. Hospedar o Aplicativo na Nuvem Azure

- Provisione um plano de Serviço de Aplicativo e um aplicativo web no Serviço de Aplicativo do Azure utilizando os comandos da CLI do Azure.
  
#### 7.1. Criando um plano do Serviço de Aplicativo:

Utilize o comando az appservice plan create para criar um novo plano do Serviço de Aplicativo usando o nível gratuito do Windows.

![criado appservice](/imagens/appservice_creat.png)

#### 7.2. Criando um aplicativo web:

Utilize o comando az webapp create para provisionar um aplicativo web em seu Plano do Serviço de Aplicativo.

![criado appservice](/imagens/webapp_create.png)

### 8. Configurar Variáveis de Ambiente na Nuvem

- Adicione configurações de aplicativo referentes às variáveis de ambiente utilizando o comando `az webapp config appsettings set`.
  
![Varaivel de ambiente mudando no azure](/imagens//alterando_variaveis.png)

### 9. Ativar Protocolo WebSocket e HTTPS

- Utilize os comandos `az webapp config set` e `az webapp update` para ativar o protocolo WebSocket e configurar para aceitar exclusivamente solicitações HTTPS.
  
![config1](/imagens/config_1.png)

![config1](/imagens/config_2.png)

### 10. Verificar o Status do Aplicativo Web

- Execute o comando `az webapp show` para garantir que o aplicativo web esteja em execução.

### 11. Acessar o Aplicativo na Nuvem

- Acesse https://<seu_nome_de_aplicativo_web>.azurewebsites.net em um navegador para visualizar o aplicativo web hospedado na nuvem Azure.

Com esses passos, você configurou com sucesso seu ambiente de desenvolvimento local e implantou o aplicativo web na nuvem Azure para visualização de dados do Azure IoT Hub. Aproveite a análise eficaz e interativa dos dados coletados!
