# Лабораторная работа №1. Основы HTTP

- [Лабораторная работа №1](#лабораторная-работа-1-основы-http)
    - [Задания](#задания)
    - [Примеры использования](#примеры-использования)
    - [Список использованных источников](#список-использованных-источников)

## Задания

### Задание №1. Анализ HTTP-запросов

1. Зайдите на сайт [http://sandbox.usm.md/login](http://sandbox.usm.md/login).
2. Откройте вкладку `Network` в инструментах разработчика браузера.
3. Введите неверные данные для входа (например, `username: student`, `password: studentpass`).
4. Проанализируйте запросы, которые были отправлены на сервер.
5. Ответьте на следующие вопросы:
   - Какой метод HTTP был использован для отправки запроса?
   - Какие заголовки были отправлены в запросе?
   - Какие параметры были отправлены в запросе?
   - Какой код состояния был возвращен сервером?
   - Какие заголовки были отправлены в ответе?
6. Повторите шаги 3-5, введя верные данные для входа (`username: admin`, `password: password`).

### Задание №2. Составление HTTP-запросов

1. Составьте `GET`-запрос к серверу по адресу `http://sandbox.com`, указав в заголовке `User-Agent` ваше имя и фамилию.
2. Составьте `POST`-запрос к серверу по адресу `http://sandbox.com/cars`, указав в теле запроса следующие параметры:
   - `make: Toyota`
   - `model: Corolla`
   - `year: 2020`
3. Составьте `PUT`-запрос к серверу по адресу `http://sandbox.com/cars/1`, указав в заголовке `User-Agent` ваше имя и фамилию, в заголовке `Content-Type` значение `application/json` и в теле запроса следующие параметры:
   ```json
   {
     "make": "Toyota",
     "model": "Corolla",
     "year": 2021
   }
   ```
4. Напишите один из возможных вариантов ответа сервера следующий запрос.
   ```http
   POST /cars HTTP/1.1
   Host: sandbox.com
   Content-Type: application/json
   User-Agent: John Doe
   model=Corolla&make=Toyota&year=2020
   ```
   Предположите ситуации, когда сервер может вернуть HTTP-коды состояния 200, 201, 400, 401, 403, 404, 500.

### Задание №3. Дополнительное задание. HTTP_Quest

> [!TIP]
> Пройдите квест отправляя запросы на сервер.

1. Отправьте `POST`-запрос на сервер по адресу `http://sandbox.usm.md/quest`, указав в заголовке User-Agent вашу фамилию и имя (Например `User-Agent: John Doe`).

```http
POST /quest HTTP/1.1
Host: sandbox.usm.md
User-Agent: John Doe
```

**curl**:

```bash
curl -X POST http://sandbox.usm.md/quest -H "User-Agent: John Doe"
```

2. Следуйте инструкциям на сервере, выполняя их по порядку.
3. В конце квеста Вам будет показано секретное слово, которое Вы должны будете предоставить в отчете.

_Примечание к заданию 3_:

1. Используйте инструмент `curl`, `postman` или любой другой инструмент для отправки запросов.
2. Вы можете начинать квест заново, выполнив первый шаг.

## Примеры использования

### Задание №1. Анализ HTTP-запросов

![image](https://github.com/user-attachments/assets/01b3bfb2-4478-4b32-ace5-6c33715d9374)

   - Какой метод HTTP был использован для отправки запроса?  `POST`
   - Какие заголовки были отправлены в запросе? 
![image](https://github.com/user-attachments/assets/98865017-b942-4e27-9116-5ce2b71b0b98)

   - Какие параметры были отправлены в запросе?
![image](https://github.com/user-attachments/assets/f466d300-0f29-44a5-a265-43a301f15785)

   - Какой код состояния был возвращен сервером? `401 Unauthorized`
   - Какие заголовки были отправлены в ответе? `keep-alive`, `text/plain;charset=UTF-8`, `Thu, 12 Sep 2024 17:18:00 GMT`,
`nginx/1.24.0 (Ubuntu)`, `chunked`

![image](https://github.com/user-attachments/assets/c0ee8c0c-fd12-4224-801c-8e6d8e54748e)

   - Какой метод HTTP был использован для отправки запроса? `POST`
   - Какие заголовки были отправлены в запросе? 
![image](https://github.com/user-attachments/assets/a4d515c6-c533-46df-8043-4b6935dfc1ae)

   - Какие параметры были отправлены в запросе?
![image](https://github.com/user-attachments/assets/a8352142-9948-4d84-8541-b8e43db4efcd)

   - Какой код состояния был возвращен сервером? `200 OK`
   - Какие заголовки были отправлены в ответе?
![image](https://github.com/user-attachments/assets/d8ee900a-bae8-43db-a015-09aebb60b951)

### Задание №2. Составление HTTP-запросов

`GET`
```http
GET / HTTP/1.1
Host: sandbox.com
User-Agent: Nichita Neboga
```
`POST`
```http
POST /cars HTTP/1.1
Host: sandbox.com

model=Corolla&make=Toyota&year=2020
```
`PUT`
```http
PUT /cars/1 HTTP/1.1
Host: sandbox.com
User-Agent: Nichita Neboga
Content-Type: application/json
{
    "make": "Toyota",
    "model": "Corolla",
    "year": 2021
}
```

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "status": "success",
    "car": {
        "make": "Toyota",
        "model": "Corolla",
        "year": 2020
    }
}

```
200 OK - Запрос на получение данных о машине прошел успешно.

201 Created - Новый автомобиль добавлен в базу данных.

400 Bad Request - Запрос неверно сформирован.

401 Unauthorized - Пользователь не предоставил корректные учетные данные.

403 Forbidden - У пользователя нет прав для выполнения данного запроса.

404 Not Found - Запрашиваемого автомобиля не существует в базе данных.

500 Internal Server Error - Сбой базы данных.

### Задание №3. Дополнительное задание. HTTP_Quest

![image](https://github.com/user-attachments/assets/6d60bb74-521a-4b10-8389-1e78b99ff44d)


```http
curl -X POST http://sandbox.usm.md/quest/login  -H "Authorization: Bearer BwgOPAERI0U9ESsOCjU="
```

![image](https://github.com/user-attachments/assets/68fd7763-0610-49df-a8a2-804e0b490a97)

```http
curl -X PUT http://sandbox.usm.md/quest/age -H "Authorization: Bearer BwgOPAERI0U9ESsOCjU=" -d "age=21"
```

![image](https://github.com/user-attachments/assets/a2168116-e134-4805-a8ee-eef6dc8b4eca)

![image](https://github.com/user-attachments/assets/061edf0f-2fce-46ab-a76d-89e2b3acb4e8)

<details>
<summary>Секретное слово</summary>
JyUMHgw9AkUCBBYbAkBEfl4=
</details>

## Список использованных источников

https://github.com/MSU-Courses/frameworks-for-web-development/blob/main/ru/01_http_basics/01_01_introduction.md

https://github.com/MSU-Courses/frameworks-for-web-development/blob/main/ru/01_http_basics/01_02_client_server.md

https://github.com/MSU-Courses/frameworks-for-web-development/blob/main/ru/01_http_basics/01_03_http.md

https://github.com/MSU-Courses/frameworks-for-web-development/blob/main/ru/01_http_basics/01_04_curl.md
