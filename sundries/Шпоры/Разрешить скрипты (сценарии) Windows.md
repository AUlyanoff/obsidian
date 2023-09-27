из командной строки запускаем powerShell с правами администратора
powershell "start-process powershell -verb runas"

далее из powerShell выдаем команду
Set-ExecutionPolicy Unrestricted

для возврата в состояние запрета скриптов (сценариев)
Set-ExecutionPolicy Restricted