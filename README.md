# Sausage Store

![image](https://user-images.githubusercontent.com/9394918/121517767-69db8a80-c9f8-11eb-835a-e98ca07fd995.png)


## Technologies used

* Frontend – TypeScript, Angular.
* Backend  – Java 16, Spring Boot, Spring Data.
* Database – H2.

## Installation guide
### Backend

Install Java 16 and maven and run:

```bash
cd backend
mvn package
cd target
java -jar sausage-store-0.0.1-SNAPSHOT.jar
```

### Frontend

Install NodeJS and npm on your computer and run:

```bash
cd frontend
npm install
npm run build
npm install -g http-server
sudo http-server ./dist/frontend/ -p 80 --proxy http://localhost:8080
```

Then open your browser and go to [http://localhost](http://localhost)

### Развёртывание и запуск приложения в Kubernetes
Выполняется в рамках [workflow](.github/workflows/deploy.yaml) GitHUB actions.
MongoDB инициализируется с помощью скрипта в docker-entrypoint, т.е. развёртывание полностю автоматизированно.
### Чувствительные переменные
Из helm-чарта убраны пароли, они подставляются на этапе развёртывания из secrets в GitHUB actions.
Запущенное приложение доступно по ссылке - [https://front-sshutdownow.2sem.students-projects.ru/](https://front-sshutdownow.2sem.students-projects.ru/) и работает: фронтенд отдаёт список сосисок, можно оформить заказ на сосиски.
