# Postman.
__HW_1__

_Создать запросы в Postman._

- Protocol: http
- IP: 162.55.220.72
- Port: 5005

__EP_1__
- Method: GET
- EndPoint: /get_method
- request url params: 
 - name: str
 - age: int

- response: 

		[
  		“Andrey”,
  		“43”
		]

==================

__EP_2__
- Method: POST
- EndPoint: /user_info_3
- request form data: 
 - name: str
 - age: int
 - salary: int

- response: 

		{'name': ""Andrey"",
          'age': 43,
          'salary': 1000,
          'family': {'children': [['Alex', 24], ['Kate', 12]],
                     'u_salary_1_5_year': salary * 4}}


==================

__EP_3__
- Method: GET
- EndPoint: /object_info_1
- request url params: 
 - name: str
 - age: int
 - weight: int

        response: 
        {'name': name,
                  'age': age,
                  'daily_food': weight * 0.012,
                  'daily_sleep': weight * 2.5}


==================

__EP_4__
- Method: GET
- EndPoint: /object_info_2
- request url params: 
 - name: str
 - age: int
 - salary: int

        response: 
        {'start_qa_salary': salary,
                  'qa_salary_after_6_months': salary * 2,
                  'qa_salary_after_12_months': salary * 2.7,
                  'qa_salary_after_1.5_year': salary * 3.3,
                  'qa_salary_after_3.5_years': salary * 3.8,
                  'person': {'u_name': [user_name, salary, age],
                             'u_age': age,
                             'u_salary_5_years': salary * 4.2}
                  }


==================

__EP_5__
- Method: GET
- EndPoint: /object_info_3
- request url params: 
 - name: str
 - age: int
 - salary: int

        response: 
        {'name': name,
                  'age': age,
                  'salary': salary,
                  'family': {'children': [['Alex', 24], ['Kate', 12]],
                             'pets': {'cat':{'name':'Sunny',
                                             'age': 3},
                                      'dog':{'name':'Luky',
                                             'age': 4}},
                             'u_salary_1_5_year': salary * 4}
                  }


==================

__EP_6__
- Method: GET
- EndPoint: /object_info_4
- request url params: 
 - name: str
 - age: int
 - salary: int

        response: 
        {'name': name,
                  'age': int(age),
                  'salary': [salary, str(salary * 2), str(salary * 3)]}


==================

__EP_7__
- Method: POST
- EndPoint: /user_info_2
- request form data: 
 - name: str
 - age: int
 - salary: int

        response: 
        {'start_qa_salary': salary,
                  'qa_salary_after_6_months': salary * 2,
                  'qa_salary_after_12_months': salary * 2.7,
                  'qa_salary_after_1.5_year': salary * 3.3,
                  'qa_salary_after_3.5_years': salary * 3.8,
                  'person': {'u_name': [user_name, salary, age],
                             'u_age': age,
                             'u_salary_5_years': salary * 4.2}
                  }
