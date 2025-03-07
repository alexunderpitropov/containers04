# Лабораторная работа №4: Запуск контейнера Ubuntu с Apache в Docker

**Питропов Алексаднр,группа I2302**  
**Дата выполнения:_07.03.2025_**

## Цель работы
Данная лабораторная работа призвана напомнить основные команды ОС Debian/Ubuntu. Также она позволит познакомиться с Docker и его основными командами.

## Задание
Запустить контейнер Ubuntu, установить Web-сервер Apache и вывести в браузере страницу с текстом "Hello, World!".

## Подготовка
Для выполнения данной работы необходимо иметь установленный на компьютере Docker.

## Выполнение
### 1. Создание репозитория
Создаём репозиторий `containers04` на GitHub и клонируем его на локальный компьютер:

```sh
 git clone https://github.com/alexunderpitropov/containers04.git
 cd containers04
```
Создаём файл `README.md` и добавляем описание работы.

### 2. Запуск контейнера Ubuntu
В терминале запускаем контейнер Ubuntu с пробросом порта 8000 на 80:

```sh
docker run -ti -p 8000:80 --name containers04 ubuntu bash
```
![image](https://i.imgur.com/hFMeENg.jpeg)
### 3. Установка и запуск Apache
В контейнере выполняем команды:

```sh
apt update                # Обновление списка пакетов
apt install apache2 -y    # Установка Apache
service apache2 start     # Запуск Apache
```
![image](https://i.imgur.com/LyNr93k.jpeg)
![image](https://i.imgur.com/LjGqwTA.jpeg)
Открываем браузер и переходим по адресу: `http://localhost:8000`. Должна загрузиться стандартная страница Apache.

![image](https://i.imgur.com/8OXhJYE.jpeg)

### 4. Добавление страницы "Hello, World!"
Выполняем команды:

```sh
ls -l /var/www/html/  # Проверяем содержимое папки с веб-страницами

echo '<h1>Hello, World!</h1>' > /var/www/html/index.html  # Создаём страницу
```

![image](https://i.imgur.com/yDncLac.jpeg)

Обновляем страницу в браузере. Теперь должно отобразиться `Hello, World!`.

![image](https://i.imgur.com/k90oGHH.jpeg)

### 5. Просмотр настроек Apache

```sh
cd /etc/apache2/sites-enabled/
cat 000-default.conf
```

На экране отобразится конфигурационный файл Apache.

### 6. Завершение работы
Выходим из контейнера:

```sh
exit
```

Проверяем список контейнеров:

```sh
docker ps -a
```

![image](https://i.imgur.com/tSKv5go.jpeg)

Удаляем контейнер:

```sh
docker rm containers04
```

![image](https://i.imgur.com/K78MBO0.jpeg)

## Выводы
В ходе лабораторной работы был запущен контейнер Ubuntu, установлен и запущен сервер Apache, создана и отображена веб-страница "Hello, World!". Также были изучены основные команды работы с Docker.

## Библиография

- [Официальная документация Docker](https://docs.docker.com/)
- [Docker Hub – репозиторий образов](https://hub.docker.com/)
- [Официальная документация Apache HTTP Server](https://httpd.apache.org/docs/)
- [DigitalOcean – руководство по установке Apache в Docker](https://www.digitalocean.com/community/tutorials/docker-explained-how-to-containerize-and-use-apache-on-ubuntu)
- [ChatGPT](https://chat.openai.com)
