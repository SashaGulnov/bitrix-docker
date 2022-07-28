# bitrix-docker

- Выполните настройку окружения

Скопируйте файл `.env.example` в `.env`

```
cp .env.example .env
```

- Запустите bitrix-docker

```
docker-compose up --build -d
```

## Востановление bitrix

Bitrix проект нужно расположить в папке `www`

> При востановлениии необходимо в окне создания базы данных в графе "Сервер" 
`localhost` заменить на `mysql` (так как контейнер поднятый в сети имеет название `mysql`)