### скачать проект
git clone --recurse-submodules -j8 http://gitlab.local/iOS/MdmServer-v3[.git]


### перед выгрузкой новой локальной ветки, 
нужна будет команда
git push —set-upstream имя ветки


### скачать удалённую ветку
git fetch origin release/6.0.1-bug:release/6.0.1-fix
скачивается с удаленного репозитария (origin) ветка release/6.0.1-bug
после двоеточия указано имя новой локальной ветки release/6.0.1-fix, которая будет создана этой командой

### обновить подмодули
git submodule update --recursive --init

### перенести в ветку два файла из другой ветки 
(перенос произойдёт в текущую ветку)
git checkout feature/test_api_v2 src/app/portal/user_agreement_dao.py src/app/api/v2/user_agreement.py
из ветки feature/test_api_v2
переносятся src/app/portal/user_agreement_dao.py и src/app/api/v2/user_agreement.py
и далее фиксируем перенос этих двух файлов
git commit -m "31327 bugfix изменение значения HTTP=475 и анализ флага использования ПС att-1"

### переименовать последний коммит
`git commit --amend -c HEAD`


### отменить последний коммит
$ git reset --mixed HEAD~1
--mixed изменения, содержащиеся в отменяемом коммите, НЕ должны исчезнуть
HEAD~1  значит, что HEAD должен быть переключен на «коммит перед самым последним»

### Полное удаление последнего коммита,
включая все изменения файлов данного коммита:
git reset --hard HEAD~1

### Изменить сообщение последнего коммита
git commit --amend
Открывает редактор сообщений коммита.

### Перечень коммитов за один день
git log --since="1 days" [-p покажет различия]

### Перечень коммитов "одной строкой каждый"
git log --pretty=oneline

### Перечень коммитов "одной строкой каждый" за один день
git log --pretty=oneline --since="1 days"

### Показать дерево всех коммитов
git log --oneline --decorate -graph --all

### Посмотреть ветки
git branch -a

### Как удалить ветку
- локальную 
  git branch -d develop-uam
- удалённую
  git push origin --delete develop-uam

### Разрезолвить, взяв их файл functional/app_flags.xlsx
AUlyanov@AUlyanov MINGW64 /d/projects/combat/SafePhone-requirements (develop-uam|MERGING)
$ git checkout -m --theirs -- functional/app_flags.xlsx
fatal: git checkout: --ours/--theirs, --force and --merge are incompatible when
checking out of the index.

AUlyanov@AUlyanov MINGW64 /d/projects/combat/SafePhone-requirements (develop-uam|MERGING)
$ git checkout --theirs -- functional/app_flags.xlsx

AUlyanov@AUlyanov MINGW64 /d/projects/combat/SafePhone-requirements (develop-uam|MERGING)
$ git add functional/app_flags.xlsx

### Внесите изменения
git add . # или добавьте файлы по отдельности.
git commit --amend --no-edit
Теперь последний коммит содержит ваши изменения.
ВНИМАНИЕ! Никогда не изменяйте опубликованные коммиты.

### удалить тэг из удалённого репозитория
git push origin --delete <tagname>

### удалить тэг из локального репозитория
git tag -d <tagname>

### узнать последний тэг ветки
git describe --tags --abbrev=0

###  поставить тэг на коммит
git tag -a 8.2 c608ab1

### запушить тэг
git push origin <tagname>


### Добавить сабмодуль
git submodule add `http://gitlab.local/SafePhone-common/DbApi` `json`
git add `.gitmodules` `src/json`
git commit -m "add repo json"

### To remove a submodule you need to

1. Delete the relevant section from the `.gitmodules` file.
2. Stage the `.gitmodules` changes:  
    `git add .gitmodules`
3. Delete the relevant section from `.git/config`.
4. Remove the submodule files from the working tree and index:  
    `git rm --cached path_to_submodule` (no trailing slash).
5. Remove the submodule's `.git` directory:  
    `rm -rf .git/modules/path_to_submodule`
6. Commit the changes:  
    `git commit -m "Removed submodule <name>"`
7. Delete the now untracked submodule files:  
    `rm -rf path_to_submodule`


### Выгрузить проект во внешний репозиторий

1. `git init`
    
2. `git add .`
    
3. `git commit -m "Add all my files"`
   
4. Сделать в удалённом репо проект `your-repo-name`
    
5. `git remote add origin https://github.com/yourusername/your-repo-name.git`
   
6. `git push -u origin master`


### Забрать коммит из другой ветки
```
git cherry-pick <commit>
```
применит `<commit>` к текущей ветке

### Отменить ```cherry-pick```
```
git cherry-pick --abort
```
отменит операцию и вернёт ветку в предыдущее состояние