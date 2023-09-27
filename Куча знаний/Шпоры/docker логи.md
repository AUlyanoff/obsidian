
### что запущено
docker ps -a
отсюда брать имена компонентов для указания вывода логов

### вывод логов

в консоль в реальном времени
docker-compose logs -tf iosmdm

в файл
docker-compose logs -t iosmdm > iosmdm1.log
docker-compose logs -t smapi > smapi1.log


### остановить все контейнеры
docker-compose down -v

### запустить все контейнеры
docker-compose up -d

### посмотреть логи контейнера
docker-compose logs -f