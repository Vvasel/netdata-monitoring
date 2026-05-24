# Netdata Monitoring on VPS

Автоматизированная настройка мониторинга сервера с помощью Netdata в Docker-контейнере.

# Что делает

- Разворачивает Netdata на VPS через Docker
- Собирает метрики: CPU, RAM, сеть, диски, процессы
- Доступ к дашборду через браузер
- Автоматический перезапуск при падении

# Быстрый старт

# Требования

- VPS с Docker
- Открытый порт 19999

# Установка

```bash
docker run -d --name=netdata \
  --hostname=your-server \
  -p 19999:19999 \
  -v /proc:/host/proc:ro \
  -v /sys:/host/sys:ro \
  -v /var/run:/host/run:ro \
  --cap-add=SYS_PTRACE \
  --security-opt seccomp:unconfined \
  --restart=unless-stopped \
  netdata/netdata:latest

# Доступ

http://your-server-ip:19999
