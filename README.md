# Проект для практического вебинара DS Prod
Практика состоит из нескольких заданий, которые покрывают следующие 
темы из курса: pickle, flask, uwsgi, docker, nginx, docker-compose.

## Задания
В каждом задании необходимо заполнить недостающие фрагменты кода 
и запустить этот код с помощью команд приведенных ниже. 
Команды можно выполнять как из терминала, так и из IDE.

### 1. Обучение и сериалзизация модели, сериализация данных
Вначале мы загружаем датасет, добавляем айди объекта для использования в дальнейшем.
Разбиваем датасет на трейн и тест - на трейне обучаем модель, 
тест сериализуем для использования во время инференса моделей. 
 
Заполните пропуски в файле `/app/src/model_train.py`. 
Команды ниже выполняют обучение модели и сериализацию данных
```
cd <project_directory>/app/src/

python model_train.py 
```
В результате выполнения команд у вас в папке src должны появиться 3 файла:
- `_webinar_model.pkl`
- `_test_data.pkl`
- `_feature_order.pkl`

### 2. Flask приложение:
Заполните пропуски в файле `/app/src/server.py`. 
Команды ниже запускают flask сервер
```
cd <project_directory>/app/src/

python server.py 
```
Протестировать работу API в этом задании можно 
вручную (запросами в браузере, приведены в коде `server.py`) 
или автоматически - запуском скриптов:
```
cd <project_directory>/app/src/

python test_hello.py

python test_predict.py
```

### 3. Flask приложение в docker контейнере:
Заполните пропуски в файле `/app/flask.Dockerfile`.
Команды ниже выполняют сборку и запуск контейнера с приложением
```
cd <project_directory>/app/

docker build -t webinar_app -f flask.Dockerfile .

docker run -p 8000:8000 -it --rm --name webinar_app webinar_app
```
Тестируем работу API в этом задании можно 
вручную (запросами в браузере, приведены в коде `server.py`) 
или автоматически - запуском скриптов:
```
cd <project_directory>/app/src/

python test_hello.py

python test_predict.py
```

### 4. Flask + uwsgi приложение в docker контейнере:
Заполните пропуски в файле `/app/uwsgi.Dockerfile`.
Команды ниже выполняют сборку и запуск контейнера с приложением
```
cd <project_directory>/app/

docker build -t webinar_app_uwsgi -f uwsgi.Dockerfile .

docker run -p 8000:8000 -it --rm --name webinar_app_uwsgi webinar_app_uwsgi
```
Тестируем работу API в этом задании можно 
вручную (запросами в браузере, приведены в коде `server.py`) 
или автоматически - запуском скриптов:
```
cd <project_directory>/app/src/

python test_hello.py

python test_predict.py
```
### 5. Flask + uwsgi приложение и nginx в двух разных контейнерах:
Заполните пропуски в файле `docker-compose.yml`.
Команда ниже выполняет сборку и запуск контейнеров с приложением
```
docker-compose up --build
```
Тестируем работу API в этом задании можно 
вручную (запросами в браузере, приведены в коде `server.py`) 
или автоматически - запуском скриптов:
```
cd <project_directory>/app/src/

python test_hello.py

python test_predict.py
```