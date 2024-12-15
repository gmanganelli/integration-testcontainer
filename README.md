# Cars 

Cars project is a simple REST API project to expose one endpoint. Cars.Tests project contains an integration test for the REST API.

## Environment variables
```
export CONNECTION_STRING='Host=localhost;Port=3306;Database=carsdb;Uid=root;Pwd=password;SslMode=None'
```

### Run

```
>> curl --request POST 'http://localhost:5276/api/cars' --header 'Content-Type: application/json' --data '{\"name\": \"bmw\", \"available\" : \"true\"}'

{"id":"1",name":"bmw","available":false}
```

# Cars.Tests

## Environment variables
```
export API_URL='http://localhost:5276'
export CONNECTION_STRING='Host=localhost;Port=3306;Database=carsdb;Uid=root;Pwd=password;SslMode=None'
```

```
>> dotnet test

Starting test execution, please wait...
A total of 1 test files matched the specified pattern.
Passed!  - Failed:     0, Passed:     1, Skipped:     0, Total:     1, Duration: < 1 ms - Cars.Tests.dll (net6.0)
```

# Run integration tests using Docker
```
>> docker-compose -f docker-compose-integration.yml up --build --abort-on-container-exit

...
integration-testing-integration-1  | [xUnit.net 00:00:01.5719739]   Finished:    Cars.Tests
integration-testing-integration-1  |   Passed Cars.Tests.CarsControllerTests.testCreateCar [1 s]
integration-testing-integration-1  |   Standard Output Messages:
integration-testing-integration-1  |  Connection: http://web:5001/api/cars
integration-testing-integration-1  | 
integration-testing-integration-1  | 
integration-testing-integration-1  | 
integration-testing-integration-1  | Test Run Successful.
integration-testing-integration-1  | Total tests: 1
integration-testing-integration-1  |      Passed: 1
integration-testing-integration-1  |  Total time: 2.0870 Seconds
integration-testing-integration-1 exited with code 0
```
