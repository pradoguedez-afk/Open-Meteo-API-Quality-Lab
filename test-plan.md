# Plano de Testes — Open-Meteo API Quality Lab

## 1. Visão Geral do Projeto

Este projeto tem como objetivo realizar testes manuais de API na Open-Meteo Forecast API utilizando o Postman. O foco é validar códigos de status HTTP, estrutura das respostas, tipos de dados, informações de fuso horário, tratamento de parâmetros inválidos e tempo básico de resposta.

## 2. Objetivos dos Testes

- Validar requisições bem-sucedidas à API.
- Verificar códigos de status HTTP para requisições válidas e inválidas.
- Validar parâmetros obrigatórios e a estrutura das respostas.
- Verificar tipos de dados e informações de fuso horário.
- Avaliar o comportamento da API diante de variáveis meteorológicas ou parâmetros inválidos.
- Medir o tempo de resposta com base em um limite definido para fins de prática.

## 3. Escopo dos Testes

### Incluído no escopo

- Requisições válidas de previsão meteorológica.
- Validação dos dados de previsão por hora.
- Validação do fuso horário e do deslocamento UTC.
- Verificação dos tipos de dados das informações meteorológicas atuais.
- Validação dos metadados e da estrutura das respostas.
- Verificação de parâmetros obrigatórios ausentes.
- Testes com parâmetros e variáveis meteorológicas inválidos.
- Validação básica do tempo de resposta.

### Fora do escopo

- Testes de carga e desempenho sob alto volume de requisições.
- Testes de invasão ou análise aprofundada de segurança.
- Uso de frameworks de automação de testes.
- Testes de aplicativos móveis.
- Validação da precisão meteorológica com fontes independentes.

## 4. Ferramentas Utilizadas

- **Postman Web:** execução de requisições e validações com scripts de teste.
- **Postman Desktop Agent:** comunicação entre o Postman Web e a API.
- **Jira:** organização e acompanhamento das atividades de teste.
- **GitHub:** versionamento e publicação da documentação e das evidências.
- **Open-Meteo Forecast API:** API sob teste.

## 5. Ambiente de Testes

- Endpoint: `https://api.open-meteo.com/v1/forecast`
- Localidade utilizada: Manaus, Amazonas, Brasil.
- Latitude: `-3.119`
- Longitude: `-60.0217`
- Fuso horário esperado: `America/Manaus`
- Abordagem: testes manuais de API com validações em JavaScript no Postman.

## 6. Estratégia de Testes

Cada caso de teste é executado por meio de uma requisição HTTP no Postman. As respostas são avaliadas com assertions em JavaScript.

As validações incluem códigos de status, propriedades da resposta, tipos de dados esperados, tratamento de parâmetros e tempo de resposta.

Um caso de teste será marcado como **PASS** quando todas as validações definidas forem aprovadas. Será marcado como **FAIL** quando uma ou mais validações falharem. Os resultados devem ser confirmados no Postman antes da publicação do status final.

## 7. Critérios de Entrada e Saída

### Critérios de entrada

- O endpoint da API está acessível.
- O Postman está configurado e conectado.
- Os casos de teste e os resultados esperados estão documentados.

### Critérios de saída

- Todos os casos planejados foram executados.
- Os resultados foram registrados na documentação.
- As evidências relevantes estão vinculadas ao repositório.
- Eventuais falhas foram documentadas e analisadas.

## 8. Entregáveis

- `README.md` — apresentação e resumo do projeto.
- `test-plan.md` — estratégia, escopo e critérios dos testes.
- `test-cases.md` — cenários detalhados e resultados esperados.
- `test-evidence.md` — referências às evidências e registros de execução.
- `evidence/` — capturas de tela que apoiam os resultados dos testes.

## 9. Riscos e Limitações

- As respostas da API podem variar porque os dados meteorológicos são atualizados.
- A conexão com a internet pode afetar a execução das requisições e o tempo de resposta.
- O limite de 5.000 ms é um critério definido para este projeto de prática, não um acordo oficial de nível de serviço da Open-Meteo.
- Os resultados dependem das respostas efetivamente recebidas e das validações executadas.

## 10. Considerações Finais

Este projeto tem finalidade educacional e demonstra conhecimentos fundamentais de testes de API, documentação de casos de teste, registro de evidências e organização do fluxo de trabalho de QA.
