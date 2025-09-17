# Sensor de Cor GY-33 (TCS34725) com Raspberry Pi Pico

Este repositório contém um projeto em C para utilizar o sensor de cor GY-33 (chip TCS34725) com a placa Raspberry Pi Pico. O projeto inclui um driver modular para facilitar a integração em seus próprios projetos.

> ⚠️ **Observação:** Para detalhes maiores e aprofundados do uso do sensor, veja documentação com explicações e datasheet de referência [LABIRAS-Sensor de Cor GY-33](https://www.notion.so/labiras/Sensor-de-Cor-GY-33-22767aa6595380938884d40e893337d7).



## ✨ Funcionalidades

-   Integração com o sensor de cor GY-33 (TCS34725).

-   Leitura contínua dos valores de cor (Vermelho, Verde, Azul e Claridade).

-   Comunicação via I2C com a Raspberry Pi Pico.

-   Exemplo de detecção de cor dominante.
   
## 🛠️ Hardware Necessário

-   **Raspberry Pi Pico** ou **Pico W**
-   **Sensor de cor GY-33**
-   **Cabos/Jumpers** para conexão

## 📦 Software e Dependências

-   **Visual Studio Code**
-   **Extensão Raspberry Pi Pico/W para VS Code**
-   **Raspberry Pi Pico SDK**, **ARM GCC Compiler** e **CMake**

## 🔌 Conexões

Conecte o sensor **GY-33** à Raspberry Pi Pico utilizando a interface **I2C0**, conforme a tabela abaixo:

| Pino do GY-33 | Pino da Raspberry Pi Pico | Descrição          |
|---------------|---------------------------|--------------------|
| **VCC**           | 3V3 (OUT)                 | Alimentação (3.3V) |
| **GND**           | GND                       | Terra              |
| **SCL**           | GP1 (I2C0 SCL)            | Clock do I2C       |
| **SDA**           | GP0 (I2C0 SDA)            | Dados do I2C       |

---

**Ponto Importante:** A forma mais fácil de conectar este sensor à placa BitDogLab é usando o cabo de 4 vias no conector I2C 0.

## 🚀 Como Compilar e Executar

### Usando o VS Code com a Extensão Raspberry Pi Pico (Recomendado)

Este projeto já está configurado para a extensão oficial, tornando o processo muito simples.

1.  **Abra o Projeto:** Abra a pasta raiz do projeto no Visual Studio Code.
2.  **Prepare a Placa:** Coloque a Raspberry Pi Pico em modo **BOOTSEL** (pressione e segure o botão BOOTSEL enquanto conecta o cabo USB).
3.  **Envie o Código:** Clique no botão **`Run`** na barra de status ou use o atalho. A extensão irá compilar o código e enviá-lo automaticamente para a placa usando o `picotool`.
6.  **Visualize a Saída:** Abra o monitor serial integrado do VS Code para ver as medições de distância.

### Usando a Linha de Comando

Se preferir não usar o VS Code, você pode compilar manualmente.

1.  **Clone o repositório:**
    ```bash
    git clone <URL_DO_SEU_REPOSITORIO>
    cd <NOME_DA_PASTA>
    ```
2.  **Crie e configure o build:**
    * Certifique-se de que a variável de ambiente `PICO_SDK_PATH` aponta para o diretório do seu SDK.
    ```bash
    mkdir build
    cd build
    cmake ..
    ```
3.  **Compile:**
    ```bash
    make
    ```
4.  **Carregue o firmware (`.uf2`):**
    -   Coloque a Pico em modo **BOOTSEL**.
    -   Copie o arquivo `build/seu_projeto.uf2` para o drive que a Pico montou no seu sistema.

## 📂 Estrutura do Projeto

```
.
├── .vscode/               # Arquivos de configuração do VS Code para a extensão
├── build/                 # Diretório (ignorado) onde os arquivos de compilação são gerados
├── inc/                   # Arquivos de cabeçalho (.h)
│   └── color_sensor.h
├── src/                   # Arquivos de código-fonte (.c)
│   ├── color_sensor.c
│   └── main.c
├── .gitignore             # Arquivos e pastas ignorados pelo Git
├── CMakeLists.txt         # Arquivo de configuração do CMake para o projeto
├── LICENSE                # Licença do projeto
└── pico_sdk_import.cmake  # Script para importar o SDK do Pico

```
## 📄 Licença
Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.
