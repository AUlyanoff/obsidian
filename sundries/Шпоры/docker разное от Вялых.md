
### если нет места
docker system prune -a

#!/bin/bash

### 2022-08-29
Этот файл используется для ручной построчной отладки (копи-паст строк в bash) сборки Докером, например, на 10.17.7.195 машине
### всё делается от root



### каталог сборки
cd /root/_sm/safephone-arm

docker system prune -a

git pull

### при необходимости
docker build --progress=plain -f debian-python.Dockerfile -t java_python2_yaml:$(git describe --tags --abbrev=0) .

### при изменении исходников
docker build --progress=plain -f debian-gradle.Dockerfile -t sm_gradle:$(git describe --tags --abbrev=0) .

### для получения сборки АРМ в докере
docker build --progress=plain --target runtime-requirements -f debian.Dockerfile -t docker-registry.niisokb.ru/emm/arm:$(git describe --tags --long --always) .

echo "ARM_VERSION=$(git describe --tags --long --always)" >> /root/sp-arm/.env

export VAR_ARM_VERSION=$(git describe --tags --long --always)

### сохранить образ в файл
docker save docker-registry.niisokb.ru/emm/arm:$VAR_ARM_VERSION | gzip > ../arm-$VAR_ARM_VERSION.tar.gz

docker image push docker-registry.niisokb.ru/emm/arm:$VAR_ARM_VERSION

### каталог запуска сборки
cd /root/sp-arm/

#echo "SUBNET_PREFIX=10.251.123" > .env
#echo "BIND_ADDR=10.17.7.195" >> .env
#echo "NGINX_VERSION=1.3.1-2-gbc0b72f" >> .env
#echo "MDM_SERVER_VERSION=6.0.0-14-g1fa32d3" >> .env
#echo "SOCKET_SERVER_VERSION=5.0-3.g2f4ebd8" >> .env
#echo "POSTGRES_VERSION=11" >> .env
#echo "SCEP_VERSION=1.0-3-ge9eec54" >> .env
#echo "WINMDM_VERSION=5.0-8-gabb28e6" >> .env
#echo "FCM_PUSH_SERVER_VERSION=4.4-6-gb3d6dc3" >> .env
#echo "ARM_VERSION=6.1-396-g33f067b" >> .env


docker-compose down -v

docker-compose up -d

docker-compose logs arm

# docker-compose down -v && docker-compose up -d


## ВСПОМОГАТЕЛЬНО 

spring.config.location=classpath:default.properties,file:"D:/_vpv/sp/safephone/safephone-arm/scripts/vpv.dev.yml",file:"D:/_vpv/sp/safephone/safephone-arm/scripts/vpv.dev.logging.yml"
  #--xxx.logging.config=classpath:logback-spring.groovy
  #--spring.profiles.active="postgresql"
  #--safephone.db.host=10.17.7.86
  #--safephone.db.name=sphone
  #--safephone.db.port=5432
  #--safephone.db.username=mportnoy
  #--safephone.db.password=111
  #-debug

docker run -it --rm -v "$PWD/config":/config -w /app docker-registry.niisokb.ru/emm/arm:6.1-397-gc862bb7  /bin/bash

docker run -it --rm -v "$PWD/config":/config -w /app docker-registry.niisokb.ru/emm/arm:$VAR_ARM_VERSION  /bin/bash


java -server -Xms256m -Xmx256m -Duser.timezone=UTC -Djava.security.egd=file:/dev/urandom \
-jar safephone-arm.jar \
              --spring.config.location=classpath:default.properties,file:/app/system/arm.default.yml,file:/app/system/arm.yml,file:/config/arm.yml

docker run -it --rm docker-registry.niisokb.ru/emm/nginx:1.3.1-2-gbc0b72f /bin/bash