# Test Cases — Open-Meteo API Testing

## 1. Informações gerais

- **Projeto:** Open-Meteo API Testing
- **Tipo de teste:** Testes funcionais de API REST
- **Ferramenta de execução:** Postman
- **Gerenciamento dos testes:** Jira
- **API:** Open-Meteo Forecast API
- **Localidade utilizada:** Manaus, Amazonas, Brasil
- **Método HTTP principal:** GET

## 2. Objetivo

Validar o comportamento da API em cenários positivos e negativos, verificando códigos HTTP, estrutura JSON, tipos de dados, metadados geográficos, fuso horário e tempo de resposta.

## 3. Ambiente de teste

Endpoint base:

`https://api.open-meteo.com/v1/forecast`

Parâmetros utilizados em diferentes cenários:

- `latitude=-3.119`
- `longitude=-60.0217`
- `timezone=America/Manaus`

## 4. Casos de teste

### API-001 — Valid Weather Request

**Objetivo:** Validar uma requisição meteorológica válida.

**Passos:**
1. Enviar uma requisição GET com os parâmetros de localização e dados meteorológicos.
2. Verificar o código HTTP.
3. Validar a estrutura dos objetos `current` e `hourly`.
4. Conferir o fuso horário retornado.

**Resultado esperado:** HTTP 200, resposta JSON válida, campos meteorológicos essenciais presentes e fuso horário correto.

**Resultado obtido:** PASS — 5/5 asserções aprovadas.

### API-002 — Hourly Forecast Validation

**Objetivo:** Validar a estrutura e a consistência dos dados meteorológicos por hora.

**Passos:**
1. Solicitar os dados de previsão horária.
2. Verificar a presença dos arrays `time` e `temperature_2m`.
3. Conferir se os arrays possuem elementos e comprimentos correspondentes.
4. Validar os tipos de dados das temperaturas.

**Resultado esperado:** HTTP 200, arrays válidos e dados de temperatura numéricos ou nulos.

**Resultado obtido:** PASS — 5/5 asserções aprovadas.

### API-003 — Timezone Validation

**Objetivo:** Verificar o fuso horário informado na resposta.

**Passos:**
1. Enviar uma requisição GET com `timezone=America/Manaus`.
2. Validar o campo `timezone`.
3. Conferir a presença e o tipo de `utc_offset_seconds`.
4. Verificar a disponibilidade dos dados meteorológicos atuais.

**Resultado esperado:** HTTP 200, fuso horário `America/Manaus` e metadados de horário válidos.

**Resultado obtido:** Consultar os resultados salvos no Postman antes de publicar o status final.

### API-004 — Invalid Parameter Validation

**Objetivo:** Validar o tratamento de um parâmetro inválido.

**Passos:**
1. Enviar uma requisição com `current=temperature_2m_typo`.
2. Verificar o código HTTP.
3. Validar a estrutura JSON da mensagem de erro.
4. Conferir os campos `error` e `reason`.

**Resultado esperado:** HTTP 400 e resposta de erro estruturada.

**Resultado obtido:** PASS — 5/5 asserções aprovadas.

### API-005 — Missing Required Parameters

**Objetivo:** Verificar o comportamento da API quando o parâmetro `latitude` está ausente.

**Passos:**
1. Enviar uma requisição sem `latitude`.
2. Manter os demais parâmetros da consulta.
3. Verificar o código HTTP e a estrutura da resposta.
4. Validar os campos de erro.

**Resultado esperado:** HTTP 400 e resposta de erro estruturada.

**Resultado obtido:** PASS — 5/5 asserções aprovadas.

### API-006 — Current Weather Data Types

**Objetivo:** Validar os tipos de dados meteorológicos atuais e suas unidades.

**Passos:**
1. Solicitar temperatura e umidade relativa atuais.
2. Verificar a presença do objeto `current`.
3. Validar os tipos numéricos de temperatura e umidade.
4. Conferir os campos de unidades em `current_units`.

**Resultado esperado:** HTTP 200, valores numéricos e unidades presentes.

**Resultado obtido:** PASS — 5/5 asserções aprovadas.

### API-007 — Invalid Weather Variable

**Objetivo:** Validar o tratamento de uma variável meteorológica inválida.

**Passos:**
1. Enviar uma requisição com `hourly=temperature_2m_typo`.
2. Verificar o código HTTP.
3. Validar a resposta JSON e os campos de erro.

**Resultado esperado:** HTTP 400 e mensagem de erro não vazia.

**Resultado obtido:** PASS — 5/5 asserções aprovadas.

### API-008 — Response Metadata Validation

**Objetivo:** Validar os metadados geográficos e o fuso horário.

**Passos:**
1. Enviar uma requisição para as coordenadas solicitadas de Manaus.
2. Verificar a presença da latitude e longitude.
3. Validar os tipos numéricos.
4. Conferir a proximidade das coordenadas retornadas em relação às solicitadas.
5. Validar o fuso horário.

**Resultado esperado:** HTTP 200, coordenadas numéricas próximas às solicitadas e fuso horário correto.

**Resultado obtido:** PASS — 5/5 asserções aprovadas.

### API-009 — Response Time Validation

**Objetivo:** Verificar se o tempo de resposta está dentro do limite definido para o projeto.

**Passos:**
1. Enviar uma requisição GET válida.
2. Medir o tempo de resposta no Postman.
3. Verificar o código HTTP e os dados retornados.
4. Comparar o tempo observado com o limite de 5.000 ms.

**Resultado esperado:** HTTP 200 e tempo de resposta inferior a 5.000 ms.

**Resultado obtido:** PASS — 5/5 asserções aprovadas; tempo observado de 1.600 ms.

**Observação:** o limite de 5.000 ms é um critério definido para este projeto de prática, não um SLA oficial da API.

### API-010 — Response Structure Validation

**Objetivo:** Validar a estrutura geral da resposta e os campos essenciais.

**Passos:**
1. Solicitar dados meteorológicos atuais e previsão horária.
2. Verificar os metadados da resposta.
3. Validar os campos de `current`.
4. Conferir os arrays `time` e `temperature_2m` em `hourly`.
5. Verificar se os arrays possuem comprimentos correspondentes.

**Resultado esperado:** HTTP 200, campos essenciais presentes e arrays consistentes.

**Resultado obtido:** PASS — 5/5 asserções aprovadas.

## 5. Resumo dos resultados

Foram executados dez cenários de teste. Os resultados relatados foram positivos nos casos confirmados; o status de API-003 deve ser conferido no Postman antes da publicação final.

| Categoria | Cobertura |
|---|---|
| Requisições válidas | API-001, API-002 |
| Fuso horário e metadados | API-003, API-008 |
| Parâmetros inválidos ou ausentes | API-004, API-005, API-007 |
| Tipos e estrutura de dados | API-006, API-010 |
| Tempo de resposta | API-009 |

## 6. Evidências

As evidências serão organizadas em capturas de tela do Postman, mostrando as requisições, os códigos HTTP e os resultados das asserções. Os registros das atividades e resultados também serão documentados no Jira.

## 7. Observações

Este é um projeto educacional de prática de QA. Os resultados representam as execuções realizadas durante o desenvolvimento do projeto e podem variar conforme as condições de rede e disponibilidade do serviço.
