# Test Plan — Open-Meteo API Quality Lab

## 1. Project Overview

This project focuses on manual API testing of the Open-Meteo Forecast API using Postman. The objective is to validate response status codes, response structure, data types, timezone information, invalid parameters, and basic response time.

## 2. Test Objectives

- Validate successful API requests.
- Verify HTTP status codes for valid and invalid requests.
- Check required parameters and response structure.
- Validate data types and timezone information.
- Verify API behavior when invalid weather variables or parameters are provided.
- Measure basic response time using a predefined practice threshold.

## 3. Scope of Testing

### In Scope

- Valid weather forecast requests.
- Hourly forecast data.
- Timezone and UTC offset validation.
- Current weather data types.
- Response metadata and structure.
- Missing required parameters.
- Invalid parameters and weather variables.
- Basic response time validation.

### Out of Scope

- Performance and load testing under high traffic.
- Security penetration testing.
- Automated testing frameworks.
- Mobile application testing.
- Validation of meteorological accuracy against independent sources.

## 4. Tools and Environment

- **Postman Web:** API requests and test assertions.
- **Postman Desktop Agent:** Connectivity between Postman Web and the API.
- **Jira:** Test activity tracking and documentation.
- **GitHub:** Test documentation and evidence organization.
- **Open-Meteo Forecast API:** API under test.

## 5. Test Environment

- API endpoint: `https://api.open-meteo.com/v1/forecast`
- Location used: Manaus, Amazonas, Brazil.
- Latitude: `-3.119`
- Longitude: `-60.0217`
- Timezone: `America/Manaus`
- Test approach: Manual API testing with Postman scripts.

## 6. Test Approach

Each test case is executed by sending an HTTP request in Postman and evaluating the response using JavaScript assertions.

The validation includes status codes, response properties, expected data types, parameter handling, and response time.

A test is marked **PASS** when all its defined assertions pass. A test is marked **FAIL** when one or more assertions fail. Results must be confirmed in Postman before the final status is published.

## 7. Entry and Exit Criteria

### Entry Criteria

- The API endpoint is accessible.
- Postman is configured and connected.
- Test cases and expected results are documented.

### Exit Criteria

- All planned test cases have been executed.
- Results are recorded in the test documentation.
- Relevant evidence is linked in the repository.
- Any failures are documented and reviewed.

## 8. Test Deliverables

- `README.md` — project overview and summary.
- `test-plan.md` — testing strategy, scope, and criteria.
- `test-cases.md` — detailed test scenarios and expected results.
- `test-evidence.md` — evidence references and execution notes.
- `evidence/` — screenshots supporting the test results.

## 9. Risks and Limitations

- API responses may vary because forecast data changes over time.
- Network connectivity can affect request execution and response time.
- The response-time threshold of 5,000 ms is a practice criterion for this project, not an official Open-Meteo service-level agreement.
- Results depend on the actual responses and assertions observed during execution.

## 10. Final Notes

This project is intended for learning and demonstrating fundamental API testing skills, test documentation, defect observation, and QA workflow organization.
