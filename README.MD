[![Build Status](https://travis-ci.com/Denis-Sotnikov/job4j_url_shortcut.svg?branch=master)](https://travis-ci.com/Denis-Sotnikov/job4j_url_shortcut)
<br>
Описание проекта<br>
Проект представляет собой сервис для сбора статистики посещения страниц для различных зарегистрированных в системе сайтов.
Пользователь регистрирует свой сайт и конвертирует ссылки своего сайта при помощи данного сервиса, после чего он может их вставлять где угодно.
Переходя по конвертированной ссылке, пользователь попадает на данный сервис. Далее происходит инкрементация числа посещений данной страницы и последующий редирект на ассоциированную с этой ковентированной ссылкой страницу.
<br>
В ходе реализации были применены следующие технологии:
Java 14
Spring Boot 2
Spring Security & JWT authorization
Spring Data JPA
PostgreSQL
Liquibase
<br>

Используем REST API<br>

Регистрируем сайт<br>
curl --location --request POST 'http://localhost:8080/shortcuts/registration' \
--header 'Content-Type: application/json' \
--data-raw '{
    "site": "vk.com"
}'
<br>

![ScreenShot](img/registration.png)

Получаем токен<br>
curl --location --request POST 'http://localhost:8080/login' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--data-raw '{
    "login": "your_login",
    "password": "your_password"
}'<br>

![ScreenShot](img/get token.png)
<br>

Конвертируем ссылку<br>
curl --location --request POST 'http://localhost:8080/shortcuts/convert' \
--header 'Authorization: Bearer your_token\
--header 'Content-Type: application/json' \
--data-raw '{
    "address": "https://vk.com/salsaplus"
}'<br>

  ![ScreenShot](img/convert.png)
  <br>

Получаем статистику<br>
curl --location --request GET 'http://localhost:8080/shortcuts/statistic' \
--header 'Authorization: Bearer your_token\

  ![ScreenShot](img/statistic.png)
  <br><br>

