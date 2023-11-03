<h1>Руководство по развёртыванию Nextcloud с использованием docker-compose</h1>

Данный файл docker-compose.yml предназначен для удобного развёртывания Nextcloud с минимальными усилиями. В нем предусмотрены настройки для сохранения данных контейнеров (volumes) и определены переменные (environment), необходимые для автоматической установки Nextcloud.

<h1>Переменные окружения</h1>

    MYSQL_PASSWORD: Эта переменная задает пароль для базы данных MySQL.
    MYSQL_DATABASE: Данная переменная задаёт имя базы данных для Nextcloud.
    MYSQL_USER: В этой переменной вы указываете имя пользователя, для доступа к базе данных.
    MYSQL_HOST: Эта переменная указывает на контейнер, в котором работает MySQL.
    NEXTCLOUD_TRUSTED_DOMAINS: В данной переменной необходимо указать IP-адрес сервера (к примеру 192.168.0.46) либо доменное имя (к примеру my-home.nextcloud-best.ru), если вы хотите иметь доступ не только через localhost.

<h1>Переменные для автоматического создания администратора в Nextcloud</h1>

    NEXTCLOUD_ADMIN_USER: С помощью этой переменной можно создать администратора в Nextcloud.
    NEXTCLOUD_ADMIN_PASSWORD: В этой переменной задается пароль администратора. Обе переменные должны быть указаны вместе. Если вы укажете только NEXTCLOUD_ADMIN_USER, то пользователь не будет создан автоматически, и вам придется создать его вручную после развёртывания Nextcloud.

<h1>Важно!</h1>

    Переменные для контейнера MySQL и Nextcloud должны совпадать. В противном случае, автоматическая установка не начнется, и вам придется указать все параметры вручную.
    Если вас не устраивают порты, указанные в файле, вы можете изменить их в параметре "ports".
    Параметр restart: unless-stopped гарантирует, что контейнер будет автоматически перезапущен при сбое его работы, перезапуске системы или Docker. Однако, он не запустит контейнер, если вы лично его остановите или выключите.

<h1>Запуск и остановка</h1>

Чтобы развёрнуть Nextcloud, выполните следующие команды:

    Для запуска: docker compose up -d в директории, где находится файл docker-compose.yml.
    Для остановки: docker compose down.
