# Open-Meteo API Testing

Projeto de portfólio em **Quality Assurance (QA)** com foco em testes de API REST utilizando Postman e gerenciamento de atividades de teste com Jira.

## Sobre o projeto

O objetivo deste projeto é praticar testes funcionais de API, validar respostas HTTP, verificar estruturas JSON, criar asserções automatizadas e documentar os resultados dos testes.

A API utilizada é a Open-Meteo Forecast API, com consultas meteorológicas para Manaus, Amazonas, Brasil.

## Ferramentas utilizadas

- **Postman:** execução de requisições HTTP e criação de asserções automatizadas em JavaScript.
- **Jira:** organização das atividades e registro dos resultados dos testes.
- **GitHub:** documentação e apresentação do projeto.
- **Open-Meteo API:** API pública utilizada nos cenários de teste.

## Escopo dos testes

Os cenários foram planejados para cobrir:

- Requisições válidas e códigos de status HTTP.
- Estrutura e tipos de dados JSON.
- Validação de temperatura, umidade e previsão horária.
- Fuso horário e metadados geográficos.
- Tratamento de parâmetros ausentes ou inválidos.
- Tempo de resposta da API.

## Casos de teste

| ID | Cenário | Resultado observado |
|---|---|---|
| API-001 | Valid Weather Request | PASS — 5/5 |
| API-002 | Hourly Forecast Validation | PASS — 5/5 |
| API-003 | Timezone Validation | PASS — 5/5 |
| API-004 | Invalid Parameter Validation | PASS — 5/5 |
| API-005 | Missing Required Parameters | PASS — 5/5 |
| API-006 | Current Weather Data Types | PASS — 5/5 |
| API-007 | Invalid Weather Variable | PASS — 5/5 |
| API-008 | Response Metadata Validation | PASS — 5/5 |
| API-009 | Response Time Validation | PASS — 5/5 |
| API-010 | Response Structure Validation | PASS — 5/5 |

**Observação:** os resultados acima refletem os testes executados e relatados durante a prática. A evidência detalhada será organizada em capturas do Postman e registros do Jira.

## Exemplo de validação automatizada

Exemplo de asserções utilizadas nos scripts Post-response do Postman:

```javascript
pm.test("HTTP status is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Response is valid JSON", function () {
    pm.response.to.be.json;
});

pm.test("Current weather data exists", function () {
    const data = pm.response.json();
    pm.expect(data).to.have.property("current");
});
```

## Aprendizados

- Construção e execução de requisições GET.
- Validação de respostas HTTP e mensagens de erro.
- Criação de asserções automatizadas com JavaScript no Postman.
- Verificação de campos, arrays, tipos de dados e metadados.
- Registro de resultados e organização das atividades de QA com Jira.
- Documentação técnica de um projeto de testes de API.

## Próximas melhorias

- Adicionar capturas de tela dos resultados do Postman.
- Documentar os casos de teste com pré-condições, passos e resultados esperados.
- Organizar evidências e resultados detalhados.
- Ampliar a cobertura com novos cenários de teste.

## API utilizada

[Open-Meteo Forecast API — Documentação oficial](https://open-meteo.com/en/docs)

---

Projeto educacional desenvolvido para prática de testes de API e construção de portfólio em QA.
