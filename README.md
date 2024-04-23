# Тренировочный проект для работы с Git

#### Данный проект размещен в **образовательных** целях.

Основныйе задачи которые необходимо решить:

1. Изучить и понять команды Git
2. Научиться работать с Git через терминал
3. Изучить тонкие настройки такие как Actions и CI/CD
---
```
Полезные команды при работе с Git

git log - Вывод полных логов по Git
git log --oneline - Вывод сокращенных логов (хэш и описание)
git log --pretty=oneline - Вывод сокращенных логов с полным хэшом и описанием
git status - Статус файлов
git status --ignored - Показать игнорируемые файлы
```
```
Отправка
git push - отправка данных в удаленный репозиторий
git push --force - отправка данных в удаленный репозиторий и при возниковении конфликтов данные из локального репозитория перепишут данные в удаленном репозитории (НЕ РЕКОМЕНДУЕТСЯ)
git push -u origin hotfix/new - соединение данных в локальной ветке hotfix/new с веткой hotfix/new в удаленном репозитории. Если в репозитории отсутствует ветка hotfix/new, она создается в репозитории.
```
```
git filter-branch --force --index-filter \ 'git rm --cached --ignore-unmatch app.py' \ --prune-empty --tag-name-filter cat -- --all  - Удалить файл из всех коммитов (пример app.py)

rm -rf .git - рассоединиться с Git
	ssh-keygen -t ed25519 -C test@gmail.com - создание SSH ключа для аккаунта test@gmail.com
```
```

git commit --amend -m "Test write Readme and add ambed.txt" - редактирование текста последнего коммита
git commit --amend --no-edit - Добавление файла/файлов добавленных через git add - в последний коммит, без создания нового коммита.
git commit -am "commit message" - git add и git commit -m в одной команде
git rm --cached config.py - Убрать файл из отслеживания Git
git cherry-pick cb42c31 - Копирование коммита с данными и перенос в ведку в которой выполняется данная комманда
```
```
Тэги
git tag - посмотреть список тэгов
git tag v0.0- возможность поставить легковесный (простой) тэг версии
git tag -a v0.0 - возможность поставить аннотированный (большой подробный сохраняющий текст к тэгу в виде отдельного файла) тэг
git tag -a v1.3 e4019c3 - припрепить тэг к существующему коммиту (работает с -a  и без -a)
git show v0.0 - показывает текст из тэга, коммита и изменений в файлах
git push origin v0.0 - по умолчанию теги не ппередаются в репозиторий и их необходимо отправлять отдельно
git push origin --tags - отправить все тэги 
git tag -d v0.0 - удалить локальный тэг
git push origin --delete v0.0 - удалить тэг в репозитории
git checkout v0.0 - перевод файлов в состояние актуальное для данного тэга (НЕ РЕКОМЕНДУЕТСЯ)
```
```
git reset --hard 4987153   - откатить изменения до коммита 4987153
git restore --staged .\example.txt - убрать файл example.txt из очереди на сохранение (git add example.txt)
git restore .\example.txt - откатит файл до последней версии сохраненной при помощи git add и git commit
```
```
git diff - показывает изменения в файле до его сохранения при помощи git add
git diff --staged - показывает изменения в файле после его сохранения при помощи git add
git diff a9928ab 11bada1 - показывает разницу между комитами (от первого к последнему, git diff 11bada1 a9928ab(HEAD) от последнего к первому)
git diff HEAD~1 (git diff HEAD~)- предыдущий комит после последнего
git diff HEAD~5 - пятый коммит с конца
git diff feature/new master .\README.md - сравнение файла README.md из ветки feature/new с README.md из ветки master

```
```
Ветки
git branch - посмотреть список локальных веток
git branch -a - посмотреть список локальных и удаленных веток
git branch  feature/add-branch-info - создать ветку feature/add-branch-info. По умолчанию с тегом feature добавляется новый функционал, а с тегом bugfix устраняются ошибки.
git checkout -b feature/add-branch-info - создать ветку feature/add-branch-info и сразу начать работать в ней.
git checkout feature/add-branch-info - переключение на ветку feature/add-branch-info
git diff feature/add-branch-info bugfix/fix-branch - сравнить какие изменения произошли в fix-branch по отношению к add-branch-info

Объединение и удаление веток
git merge feature/add-branch-info - обединяет ветку feature/add-branch-info с той, в которой мы находимся сейчас
git merge --no-ff feature/add-branch-info - обединяет ветку feature/add-branch-info с той, в которой мы находимся сейчас и создает отдельный коммит об объединении веток (РЕКОМЕНДУЕТСЯ)
git config --add merge.ff false - отключить fast-forward в проекте
git branch -D feature/add-branch-info - удаляет ветку feature/add-branch-info
git branch -d feature/add-branch-info -  удаляет ветку в том случае, если данные из нее есть в другой ветке (нет уникальных данных).
git rebase hotfix/new - перенос данных и коммитов из одной ветки в другую
```
```
Корректная последовательность действи при работе с ветками
СОЗЛАНИЕ ВЕТКИ
git checkout master
git pull
git branch feature/new
git push -u (или --set-upstream) origin feature/new
Слияние веток
git checkout master
git pull
git merge feature/new
git push
```
[Инструкция по архитектуре веток в проекте](https://habr.com/ru/articles/106912/)

