====если необходимо снимать логи на стыке АРМ и БД (на будущее)====

Просьба переснять логи АРМ с указанием в arm.yml параметров:

logging:
  level:
    root: WARN
    jdbc:
      sqlonly: DEBUG
      audit: OFF
      connection: OFF
      sqltiming: DEBUG
    com.safephone.dao.resultcode: DEBUG


#Logging
logging:
  level:
    root: WARNING
    jdbc:
      sqlonly: DEBUG
      audit: OFF
      connection: OFF
      sqltiming: ON
    com.safephone.dao.resultcode: DEBUG


#Logging
logging:
  level:
    root: DEBUG
    jdbc:
      sqlonly: OFF
      audit: OFF
      connection: OFF
      sqltiming: DEBUG
    com.safephone.dao.resultcode: DEBUG



iosmdm:
  log: D   # уровень логирования DEBUG (D), INFO (I), WARNING (W), ERROR (E), FATAL (F, CRITICAL, C) - регистр любой



Команды для снятия логов через putty: (на ССО перейти в папку /opt/safephone/postgresql/ )

docker compose logs -t arm  > arm.log     
docker compose logs -t iosmdm  > iosmdm.log

docker compose logs -t --tail="2000" arm > arm.log
docker compose logs -t --tail="2000" iosmdm > iosmdm.log