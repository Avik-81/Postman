# Чек-лист валидных проверок API:
1. ___Проверка статус-кода ответа:___

_Убедитесь, что API возвращает ожидаемый статус-код (например, 200 для успешного запроса)._

    javascript
    pm.test("Status code is 200", function () {
        pm.response.to.have.status(200);
    });
 2. ___Проверка структуры JSON-ответа:___

_Убедитесь, что ответ содержит все необходимые ключи и имеет правильную структуру._

    javascript
    pm.test("Response has all required keys", function () {
        let jsonData = pm.response.json();
        pm.expect(jsonData).to.have.all.keys('name', 'age', 'salary', 'family');
    });
3.___Проверка типов данных:___

_Убедитесь, что все ключи имеют правильные типы данных._

    javascript
    pm.test("Check data types", function () {
        let jsonData = pm.response.json();
        pm.expect(jsonData.name).to.be.a('string');
        pm.expect(jsonData.age).to.be.a('number');
        pm.expect(jsonData.salary).to.be.a('number');
    });
4.___Проверка вложенных структур:___

_Проверка вложенных объектов и массивов на наличие правильной структуры и типов данных._

    javascript
    pm.test("Check nested structures", function () {
        let jsonData = pm.response.json();
        pm.expect(jsonData.family.children).to.be.an('array');

        jsonData.family.children.forEach(child => {
            pm.expect(child).to.be.an('array').that.has.lengthOf(2);
            pm.expect(child[0]).to.be.a('string');
            pm.expect(child[1]).to.be.a('number');
        });
    });
5.___Проверка содержимого массива:___

_Убедитесь, что массив содержит ожидаемые значения._

    javascript
    pm.test("Check array content", function () {
        let jsonData = pm.response.json();
        let expectedChildren = [['Alex', 24], ['Kate', 12]];

        pm.expect(jsonData.family.children).to.eql(expectedChildren);
    });
6. ___Проверка значения из переменной окружения:___

_Проверка значений, полученных из переменных окружения._

    javascript
    pm.test("Check environment variable", function () {
        let jsonData = pm.response.json();
        let envSalary = pm.environment.get("salary");
        pm.expect(jsonData.salary).to.eql(parseInt(envSalary, 10));
    });
7.___Проверка времени ответа:___

_Убедитесь, что API отвечает в приемлемое время._

    javascript
    pm.test("Response time is less than 200ms", function () {
        pm.expect(pm.response.responseTime).to.be.below(200);
    });
# Чек-лист невалидных проверок API:
1. ___Проверка статус-кода при невалидном запросе:___

_Убедитесь, что API возвращает корректный статус-код для невалидных запросов (например, 400 для неправильного формата данных, 401 для неавторизованного доступа)._

    javascript
    pm.test("Status code is 400 for invalid request", function () {
        pm.response.to.have.status(400);
    });
2. ___Проверка на отсутствие обязательных полей:___

_Проверьте, что API возвращает ошибку, если обязательные поля не переданы._

    javascript
    pm.test("Check response when required fields are missing", function () {
        let jsonData = pm.response.json();
        pm.expect(jsonData).to.have.property('error');
    });
3.___Проверка на неверный тип данных:___

_Убедитесь, что API обрабатывает неверные типы данных и возвращает соответствующую ошибку._

    javascript
    pm.test("Invalid data type results in error", function () {
        let jsonData = pm.response.json();
        pm.expect(jsonData).to.have.property('error');
    });
4.___Проверка на слишком большие/маленькие значения:___

_Проверьте, что API корректно обрабатывает значения, выходящие за ожидаемые границы (например, слишком большие или маленькие числа)._

    javascript
    pm.test("Check response for out-of-range values", function () {
        let jsonData = pm.response.json();
        pm.expect(jsonData).to.have.property('error');
    });
    
5. __Проверка на SQL/NoSQL инъекции:___

_Убедитесь, что API устойчиво к попыткам SQL или NoSQL инъекций._

        javascript
        pm.test("Check response for SQL injection", function () {
        pm.response.to.not.have.status(200); // Ожидаем, что запрос с инъекцией вернет ошибку
        });
        
6. __Проверка на XSS атаки:__

_Убедитесь, что API правильно обрабатывает потенциальные XSS атаки._

    javascript
    pm.test("Check response for XSS attack", function () {
        let jsonData = pm.response.json();
        pm.expect(jsonData).to.not.include('<script>');
    });
7.___Проверка на неверный формат данных:___

_Проверьте, что API возвращает ошибку при отправке данных в неверном формате (например, текст вместо JSON)._

    javascript
    pm.test("Check response for invalid data format", function () {
        pm.response.to.have.status(400);
    });
8. ___Проверка на дублирование данных:___

_Убедитесь, что API корректно обрабатывает попытки дублирования данных._

    javascript
    pm.test("Check response for duplicate data", function () {
        let jsonData = pm.response.json();
        pm.expect(jsonData).to.have.property('error');
    });
9. ___Проверка авторизации и аутентификации:__

_Убедитесь, что API правильно обрабатывает запросы без авторизации или с неверными учетными данными._

    javascript
    pm.test("Check response for unauthorized access", function () {
        pm.response.to.have.status(401);
    });
10.___Общий шаблон для невалидных проверок:___

    javascript
    pm.test("Check invalid scenarios", function () {
        let jsonData = pm.response.json();
        pm.expect(jsonData).to.have.property('error');
        pm.response.to.have.status(400); // или другой ожидаемый статус-код
    });
