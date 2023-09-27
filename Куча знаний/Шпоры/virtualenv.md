Установка VirtualEnv и VirtualEnvWrapper в Windows
pip install virtualenv
pip install virtualenvwrapper-win


Если при установке возникла ошибка 
setuptools pip failed with error code 1` error, 
используйте следующую команду, чтобы решить проблему:
pip install --upgrade setuptools


создание среды
virtualenv -p </usr/bin/python путь к Питону> venv_name
virtualenv -p python37 venv37
или
virtualenv venv_name


активация
venv_name/Scripts/activate.bat


деактивация
deactivate