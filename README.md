# Prometheus
Эта конфигурация предназначена для развертывания системы мониторинга Zabbix с использованием Docker Compose

## 1. Подготовка окружения
Убедитесь, что у вас установлены `Docker` и `Docker Compose`, если нет воспользуйтесь следующей инструкцией: https://docs.docker.com/engine/install/

Убедитесь, что `Git` установлен. Если нет, установите его: https://git-scm.com/downloads

## 2. Клонирование репозитория
Перейдите в директорию, в которой вы хотите развернуть Zabbix:
```bash
cd /opt/docker/
```
Клонируйте репозиторий с GitHub:
```bash
git clone https://github.com/A3th3rS3t/Prometheus-docker.git
```
```bash
cd Prometheus-docker
```

## 3. Запуск сервисов через Docker Compose
В директории с проектом выполните команду для запуска сервисa:
```bash
docker compose up -d
```
Это запустит контейнер:
```bash
prometheus_app — сервис grafana.
```
Создаем файл конфигурации:
```bash
touch volumes/conf/prometheus.yml
```
После выдаем права приложению на запись, для возможности создания таблиц в `volumes`:
```bash
chmod go+w volumes/*
```
И перезапускаем контейнер:
```bash
docker restart prometheus_app
```

## 4. Проверка работоспособности
Откройте браузер и перейдите по адресу: localhost:9090 (или другой порт, если вы изменили его в docker-compose.yaml)

Если что-то не работает, проверьте логи контейнеров:
```bash
docker logs prometheus_app
```

## 5. Остановка и удаление сервисов
Если вам нужно изменить порты или другие параметры, отредактируйте файл 
docker-compose.yaml и перезапустите сервисы:
```bash
docker compose down
docker compose up -d
```