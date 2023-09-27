

обновление pip
python -m pip install --upgrade pip


Чтобы установить конкретную версию пакета python, 
будь то в первый раз, обновление или понижение:
pip install --force-reinstall cheroot==8.5.2

pip install -r requirements.txt
pip install -r requirements.txt --upgrade

pip list

Создать файл с зависимостями:
pip freeze > requirements.txt

