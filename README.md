# Полезные команды при работе с Git

#### Данный проект размещен в **образовательных** целях.
---
### История и текущее состояние
```
git log - Вывод полных логов по Git
git log --oneline - Вывод сокращенных логов (хэш и описание)
git log --pretty=oneline - Вывод сокращенных логов с полным хэшом и описанием
git log --graph --all --decorate --oneline - вариация вывода логов с отрисовкой ветвей
git status - Статус файлов
git status --ignored - Показать игнорируемые файлы
```
### Отправка данных
```
git push - отправка данных в удаленный репозиторий
git push --force - отправка данных в удаленный репозиторий и при возниковении конфликтов данные из локального репозитория перепишут данные в удаленном репозитории (НЕ РЕКОМЕНДУЕТСЯ)
git push -u origin hotfix/new - соединение данных в локальной ветке hotfix/new с веткой hotfix/new в удаленном репозитории. Если в репозитории отсутствует ветка hotfix/new, она создается в репозитории.
```
### Работа с коммитами
```
git commit --amend -m "Test write Readme and add ambed.txt" - редактирование текста последнего коммита
git commit --amend --no-edit - Добавление файла/файлов добавленных через git add - в последний коммит, без создания нового коммита.
git commit -am "commit message" - git add и git commit -m в одной команде
git rm --cached config.py - Убрать файл из отслеживания Git
git cherry-pick cb42c31 - Копирование коммита с данными и перенос в ведку в которой выполняется данная комманда
```
### Тэги
```
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
### Отмена изменений
```
git revert 4987153 - отменить коммит 4987153 и вернуться к состоянию которое было до этого коммита
git reset --soft 4987153   - удалить только информацию о коммитах до коммита 4987153. Данные остануться и для сохранения их нужно закомитить.
git reset --hard 4987153   - удалить все изменения и данные до коммита 4987153
git restore --staged .\example.txt - убрать файл example.txt из очереди на сохранение (git add example.txt)
git restore .\example.txt - откатит файл до последней версии сохраненной при помощи git add и git commit
```
### Детальная информация и сравнение
```
git diff - показывает изменения в файле до его сохранения при помощи git add
git diff --staged - показывает изменения в файле после его сохранения при помощи git add
git diff a9928ab 11bada1 - показывает разницу между комитами (от первого к последнему, git diff 11bada1 a9928ab(HEAD) от последнего к первому)
git diff HEAD~1 (git diff HEAD~)- предыдущий комит после последнего
git diff HEAD~5 - пятый коммит с конца
git diff feature/new master .\README.md - сравнение файла README.md из ветки feature/new с README.md из ветки master
```
### Работа с ветками
```
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
### Корректная последовательность действи при работе с ветками
```
СОЗЛАНИЕ ВЕТКИ
git checkout master
git pull
git branch feature/new
git push -u (или --set-upstream) origin feature/new

СЛИЯНИЕ ВЕТОК

git checkout master
git pull
git merge feature/new
git push

ПРИ КОНФЛИКТЕ ВЕТОК master и feature

git checkout master
git pull
git checkout feature
git merge master
git pull
P.S. новый pull requests создавать не надо
```
### Gitignore
```
file?.txt - ? обозначает один символ. Будут проигнорированы файлы fileA.txt и file1.txt, но не file12.txt

*.jpeg - Система игнорирует все файлы с расширением jpeg

!doge.jpeg - но только не мем с Doge

file[0-2].txt - игнорировать файлы file0.txt, file1.txt и file2.txt

file[adc].txt - игнорировать файлы filea.txt, fileb.txt и filec.txt

docs/**/tmp - игнорировать файлы "docs/current/tmp", "docs/old/tmp", а также "docs/old/saved/a/b/c/d/tmp" и даже "docs/tmp", потому что ноль вложенных папок тоже подходит

docs/*/tmp - игнорировать только "docs/current/tmp" и "docs/old/tmp", файл "docs/old/saved/a/b/c/d/tmp" не попадает в правило

```
### Vim
```
git mergerool - вызов инструмента слияния коммитов (на базе Vim)
:wq - сохранение
:qa! - выход из Vim
P.S. vimdiff создаёт копию конфликтного файла с маркерами изменений и расширением .orig. Этот файл можно удалить после слияния
```
### Дополнительные команды
```
git filter-branch --force --index-filter \ 'git rm --cached --ignore-unmatch app.py' \ --prune-empty --tag-name-filter cat -- --all  - Удалить файл из всех коммитов (пример app.py)

rm -rf .git - рассоединиться с Git
	ssh-keygen -t ed25519 -C test@gmail.com - создание SSH ключа для аккаунта test@gmail.com

Формат датирования коммитов

--date=format:'%Y-%m-%d %H:%M:%S' - часовой пояс комментирующего
--date=format-local:'%Y-%m-%d %H:%M:%S' - часовой пояс текущего пользователя
git config --global alias.fulllog "log --oneline --graph --date=format-local:'%d.%m.%Y %H:%M:%S' --pretty=format:'%h - %an, %cd : %s'" - создания алиаса git fulllog
```
---
### Список литературы
[Инструкция по архитектуре веток в проекте](https://habr.com/ru/articles/106912/)  
[Инструкция по созданию алиасов](https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases)
