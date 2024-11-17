HW_3 Postman
=====

1) необходимо залогиниться
<br>POST
<br>http://162.55.220.72:5005/login
<br>login : str (кроме /)
<br>password : str

Приходящий токен необходимо передать во все остальные запросы.

===================
- дальше все запросы требуют наличие токена.

===================

2) ___http://162.55.220.72:5005/user_info___
<br>req. (RAW JSON)
<br>POST
<br>age: int
<br>salary: int
<br>name: str
<br>auth_token


          resp.
          {'start_qa_salary':salary,
           'qa_salary_after_6_months': salary * 2,
           'qa_salary_after_12_months': salary * 2.9,
           'person': {'u_name':[user_name, salary, age],
                                          'u_age':age,
                                          'u_salary_1.5_year': salary * 4}
                                          }

Тесты:
1) Статус код 200
2) Проверка структуры json в ответе.
3) В ответе указаны коэффициенты умножения salary, напишите тесты по проверке правильности результата перемножения на коэффициент.
4) Достать значение из поля 'u_salary_1.5_year' и передать в поле salary запроса http://162.55.220.72:5005/get_test_user 

===================

3. ___http://162.55.220.72:5005/new_data___
<br>req.
<br>POST
<br>age: int
<br>salary: int
<br>name: str
<br>auth_token

Resp.

    {'name':name,
      'age': int(age),
      'salary': [salary, str(salary*2), str(salary*3)]}

Тесты:
1) Статус код 200
2) Проверка структуры json в ответе.
3) В ответе указаны коэффициенты умножения salary, напишите тесты по проверке правильности результата перемножения на коэффициент.
4) проверить, что 2-й элемент массива salary больше 1-го и 0-го

===================

4) ___http://162.55.220.72:5005/test_pet_info___
<br>req.
<br>POST
<br>age: int
<br>weight: int
<br>name: str
<br>auth_token


<br>Resp.

    {'name': name,
     'age': age,
     'daily_food':weight * 0.012,
     'daily_sleep': weight * 2.5}


Тесты:
1) Статус код 200
2) Проверка структуры json в ответе.
3) В ответе указаны коэффициенты умножения weight, напишите тесты по проверке правильности результата перемножения на коэффициент.

===================

5) ___http://162.55.220.72:5005/get_test_user___
<br>req.
<br>POST
<br>age: int
<br>salary: int
<br>name: str
<br>auth_token

<br>Resp.

    {'name': name,
     'age':age,
     'salary': salary,
     'family':{'children':[['Alex', 24],['Kate', 12]],
     'u_salary_1.5_year': salary * 4}
      }

Тесты:
1) Статус код 200
2) Проверка структуры json в ответе.
3) Проверить что занчение поля name = значению переменной name из окружения
4) Проверить что занчение поля age в ответе соответсвует отправленному в запросе значению поля age

===================

