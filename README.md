Руководство по развёртыванию Nextcloud с использованием docker-compose

Данный файл docker-compose.yml предназначен для удобного развёртывания Nextcloud с минимальными усилиями. В нем предусмотрены настройки для сохранения данных контейнеров (volumes) и определены переменные (environment), необходимые для автоматической установки Nextcloud.
Переменные окружения

    MYSQL_PASSWORD: Эта переменная задает пароль для базы данных MySQL, где будет храниться информация Nextcloud. Она также определяет имя базы данных для Nextcloud.
    MYSQL_USER: С этой переменной вы указываете имя пользователя, созданного в MySQL для доступа к базе данных.
    MYSQL_HOST: Эта переменная указывает на контейнер, в котором работает MySQL. В данном случае, это контейнер MySQL.

Переменные для администратора Nextcloud

    NEXTCLOUD_ADMIN_USER: С помощью этой переменной можно создать администратора Nextcloud.
    NEXTCLOUD_ADMIN_PASSWORD: С этой переменной задается пароль администратора. Обе переменные должны быть указаны вместе. Если вы укажете только NEXTCLOUD_ADMIN_USER, то администратор с правами не будет создан автоматически, и вам придется создать его вручную после развёртывания Nextcloud.

Важно

    Переменные для контейнера MySQL и Nextcloud должны совпадать. В противном случае, автоматическая установка не начнется, и вам придется указать все параметры вручную.
    Если вас не устраивают порты, указанные в файле, вы можете изменить их в параметре "ports".
    Параметр restart: unless-stopped гарантирует, что контейнер будет автоматически перезапущен при сбое его работы, перезапуске системы или Docker. Однако, он не запустит контейнер, если вы явно его остановите или выключите.

Запуск и остановка

Чтобы развёрнуть Nextcloud, выполните следующие команды:

    Для запуска: docker compose up -d в директории, где находится файл docker-compose.yml.
    Для остановки: docker compose down.

Следуя этому руководству, вы сможете легко развернуть Nextcloud с минимальными усилиями и настроить его по своим потребностям.
