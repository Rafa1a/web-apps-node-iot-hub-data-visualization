# Documentação do Projeto: Visualização de Dados do Azure IoT Hub

Este documento fornece um roteiro de prática para configurar e executar um aplicativo web para visualização de dados provenientes do Azure IoT Hub. Siga os passos abaixo para configurar seu ambiente de desenvolvimento e implantar o aplicativo na nuvem Azure.

## Pré-requisitos

- Conta no Microsoft Azure.
- Navegador Web (Google Chrome, Firefox, MS Edge, Safari ou Opera).
- Visual Studio Code (VS Code).
- Raspberry Pi Azure IoT Online Simulator.[Raspberry Pi Azure IoT Online Simulator](https://azure-samples.github.io/raspberry-pi-web-simulator/#GetStarted)

## Procedimentos
- Antes Precisa criar hub IOT no azure 
### 1. Baixar e Configurar o Código-fonte

- Acesse o repositório do aplicativo web no GitHub: [Azure Samples - Web Apps Node IoT Hub Data Visualization](https://github.com/Azure-Samples/web-apps-node-iot-hub-data-visualization).
- Clone ou faça o download do código-fonte.
- Descompacte os arquivos em uma pasta de sua escolha.
- Abra a pasta do aplicativo Web em sua IDE preferida, como o Visual Studio Code.

### 3. Adicionar Grupo de Consumidores ao Hub IoT

- Execute o seguinte comando na CLI do Azure para adicionar um grupo de consumidores ao ponto de extremidade interno do hub IoT:
