**api-mock-study**
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Repositório: [https://github.com/Devrodd/api-mock-study](https://github.com/Devrodd/api-mock-study)

Projeto de estudo para mock de API de registro de veículos usando WireMock.

---

## Índice

1. [Funcionalidades](#funcionalidades)
2. [Pré-requisitos](#pré-requisitos)
3. [Instalação](#instalação)
4. [Execução](#execução)
5. [Cenários de Mock](#cenários-de-mock)
6. [Endpoints Expostos](#endpoints-expostos)
7. [Contribuição](#contribuição)
8. [Licença](#licença)

---

## Funcionalidades

* Simulação de cadastro de veículos com comportamentos pré-definidos.
* Diferenciação de status de resposta conforme o valor do parâmetro `model`.
* Rápida configuração via JAR standalone do WireMock.

---

## Pré-requisitos

* **Java 11+** instalado na máquina. Verifique com:

  ```bash
  java -version
  ```
* **WireMock Standalone JAR** (versão 3.9.1) disponível no diretório do projeto ou baixado em [WireMock Releases](https://repo1.maven.org/maven2/com/github/tomakehurst/wiremock-standalone/3.9.1/).

---

## Instalação

1. Clone este repositório:

   ```bash
   git clone https://github.com/Devrodd/api-mock-study.git
   ```
2. Acesse a pasta do projeto:

   ```bash
   cd nome-do-projeto
   ```
3. Certifique-se de ter o arquivo `wiremock-standalone-3.9.1.jar` no diretório raiz do projeto.

---

## Execução

Para iniciar o servidor mock, execute:

```bash
java -jar wiremock-standalone-3.9.1.jar
```

Por padrão, o WireMock subirá na porta `8080`. Para alterar a porta, adicione a flag `--port`:

```bash
java -jar wiremock-standalone-3.9.1.jar --port 9090
```

---

## Cenários de Mock

Este mock responde diferentes códigos HTTP conforme o valor enviado no campo `model` de um cadastro de veículo:

|    `model` | Método | Endpoint    | Resposta HTTP             | Descrição                 |
| ---------: | :----- | :---------- | :------------------------ | :------------------------ |
|  **fusca** | POST   | `/vehicles` | 201 Created               | Cadastro bem‑sucedido     |
| **up tsi** | POST   | `/vehicles` | 500 Internal Server Error | Erro simulado de servidor |

> **Observação**: outros valores de `model` retornam um `200 OK` com um corpo padrão ou podem ser configurados conforme necessidade.

---

## Endpoints Expostos

### Cadastro de Veículo

* **URL**: `/vehicles`
* **Método**: `POST`
* **Header**: `Content-Type: application/json`
* **Body de Exemplo**:

  ```json
  {
    "brand": "Volkswagen",
    "model": "fusca",
    "year": 1978,
    "color": "Azul"
  }
  ```
* **Respostas**:

  * `201 Created` (caso `model` seja `fusca`)
  * `500 Internal Server Error` (caso `model` seja `up tsi`)
  * `200 OK` (demais casos)

---

## Contribuição

1. Fork este repositório.
2. Crie uma *branch* para sua feature (`git checkout -b feature/nome-da-feature`).
3. Faça um *commit* das suas alterações (`git commit -m 'Adiciona nova feature'`).
4. Envie para a *branch* original (`git push origin feature/nome-da-feature`).
5. Abra um Pull Request.

---

## Licença

Este projeto está licenciado sob a [MIT License](LICENSE).
