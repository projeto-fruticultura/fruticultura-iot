# PI Vale do São Francisco — IoT com Wokwi

Simulação IoT da plataforma de monitoramento climático da fruticultura do Vale do São Francisco.

## Sobre o projeto

Este repositório contém a simulação de uma placa ESP32 no Wokwi. A placa será conectada a componentes capazes de simular temperatura e umidade.

As leituras serão enviadas ao backend por HTTP em formato JSON.

## Objetivo

Desenvolver uma simulação capaz de:

- iniciar a ESP32;
- conectar a placa ao Wi-Fi simulado;
- coletar temperatura e umidade;
- identificar o sensor;
- gerar data e hora para a leitura;
- montar um objeto JSON;
- enviar os dados à API REST;
- exibir o resultado no monitor serial;
- continuar funcionando quando houver falha de conexão.

## Arquitetura

```text
Sensor simulado
       ↓
ESP32 no Wokwi
       ↓ Wi-Fi
HTTP POST com JSON
       ↓
API REST no Render
       ↓
PostgreSQL no Render
       ↓
Dashboard no Netlify
```

## Tecnologias

- Wokwi;
- ESP32;
- C++;
- Wi-Fi;
- HTTP;
- JSON;
- monitor serial;
- sensor de temperatura e umidade a definir;
- Git e GitHub.

## Componentes planejados

| Componente | Função | Status |
|---|---|---|
| ESP32 | Executar o programa e enviar as leituras | Definido |
| Sensor de temperatura e umidade | Produzir os valores climáticos | A definir |
| Wokwi | Simular a montagem e execução | Definido |
| Wi-Fi virtual | Conectar a ESP32 à internet | Definido |
| API REST | Receber as leituras | Definido |

O modelo exato do sensor e seus pinos deverão ser documentados após a escolha da equipe.

## Funcionamento esperado

1. Inicializar a comunicação serial.
2. Inicializar o sensor.
3. Conectar a ESP32 ao Wi-Fi.
4. Obter temperatura e umidade.
5. Verificar se os valores são válidos.
6. Montar o JSON.
7. Enviar uma requisição `POST`.
8. Mostrar a resposta no monitor serial.
9. Aguardar o intervalo configurado.
10. Repetir o processo.

## Exemplo de leitura

```json
{
  "sensorId": 1,
  "temperatura": 29.5,
  "umidade": 62,
  "dataHora": "2026-09-01T10:00:00"
}
```

## Endpoint planejado

```text
POST /api/leituras
```

## Estrutura do repositório

```text
pi-vale-iot-wokwi/
├── docs/
├── diagram.json
├── libraries.txt
├── sketch.ino
└── README.md
```

## Configuração prevista

```cpp
const char* WIFI_SSID = "Wokwi-GUEST";
const char* WIFI_PASSWORD = "";
const char* API_URL = "URL_DO_BACKEND/api/leituras";
```

A URL deverá ser atualizada depois que o backend for publicado no Render.

## Responsável principal

- **Integrante 5:** Wokwi, ESP32, sensores e envio HTTP.

A integração envolverá também:

- Integrante 3: implementação do endpoint;
- Integrante 4: armazenamento das leituras;
- Integrante 6: testes e validações;
- Integrantes 1 e 2: exibição das leituras no frontend.

## Testes mínimos

| Cenário | Resultado esperado |
|---|---|
| ESP32 inicializada | Mensagem aparece no monitor serial |
| Wi-Fi disponível | ESP32 conecta corretamente |
| Sensor disponível | Temperatura e umidade são exibidas |
| Leitura válida | API responde com sucesso |
| API indisponível | Erro é registrado sem travar a placa |
| Valor inválido | Leitura não é enviada ou é rejeitada |
| Novo ciclo | Outra leitura é gerada após o intervalo |
| Banco integrado | Leitura aparece no histórico |
| Frontend integrado | Leitura aparece no dashboard |

## Documentação das conexões

Após a escolha do sensor, esta seção deverá informar:

- nome e modelo;
- função;
- tensão de funcionamento;
- pino de alimentação;
- pino de terra;
- pino de dados;
- GPIO utilizado;
- biblioteca necessária;
- cuidados para evitar danos.

## Execução

1. Abrir o projeto no Wokwi.
2. Conferir o arquivo `diagram.json`.
3. Abrir o arquivo `sketch.ino`.
4. Configurar a URL da API.
5. Iniciar a simulação.
6. Abrir o monitor serial.
7. Conferir as leituras e respostas HTTP.

## Padrão de contribuição

1. Criar uma branch.
2. Alterar a montagem ou o código.
3. Executar a simulação.
4. Registrar evidências.
5. Fazer o commit.
6. Abrir um pull request.
7. Solicitar revisão.

## Status

Simulação e componentes em definição.
