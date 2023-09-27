### Полезные команды  
  
Остановить контейнер и связанные с ним службы  
   ```bush  
   docker-compose down   
   ```

Запуск контейнера с отображением в консоли логов  
   ```bush   
      docker-compose up --build  
   ```

Контейнер запущен, надо отобразить логи  
   ```bush   
      docker-compose logs -f     
   ```  

**Сохранить** образ в файловую систему (для передачи в продакшн)  
```bush   
      docker save trackstudio-report > trackstudio-report.tar  
      docker save trackstudio-report -o trackstudio-report.tar   
```  

**Добавить** на образ `trackstudio-report` тэг `2.2-5-g306fab3`  
```bush  
      docker tag trackstudio-report trackstudio-report:2.2-5-g306fab3   
```

**Удалить** образ `trackstudio-report` с тэгом `2.2-5-g306fab3`  
```bush  
      docker rmi trackstudio-report trackstudio-report:2.2-5-g306fab3
```  

Попытка зайти внутрь работающего контейнера  
```bush   
      docker run -it --rm -w /src  trackstudio-report:latest /bin/bash  
      docker run -it --rm -w /src  trackstudio-report:latest /bin/sh               *вместо run попробуйте exec   
```  

Получить от git номер сборки  
```bush  
      echo "ver=$(git describe --tags --long --always)" > ver.txt   
```




### развернуть контейнер из образа
docker-compose up -d

### остановить контейнер и связанные с ним службы (напр., сетевые)
docker-compose down

### сохранить образ к себе
docker save trackstudio-report > trackstudio-report.tar