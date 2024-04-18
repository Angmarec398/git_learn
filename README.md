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
git status - Статус файлов
git status --ignored - Показать игнорируемые файлы
```
```
git filter-branch --force --index-filter \ 'git rm --cached --ignore-unmatch app.py' \ --prune-empty --tag-name-filter cat -- --all  - Удалить файл из всех коммитов (пример app.py)

rm -rf .git - рассоединиться с Git
	ssh-keygen -t ed25519 -C test@gmail.com - создание SSH ключа для аккаунта test@gmail.com
```
```

git commit --amend -m "Test write Readme and add ambed.txt" - редактирование текста последнего коммита
git commit --amend --no-edit - Добавление файла/файлов добавленных через git add - в последний коммит, без создания нового коммита.
git rm --cached config.py - Убрать файл из отслеживания Git
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

```
```
Ветки
git branch - посмотреть список текущих веток
git branch  feature/add-branch-info - создать ветку feature/add-branch-info. По умолчанию с тегом feature добавляется новый функционал, а с тегом bugfix устраняются ошибки.
git checkout -b feature/add-branch-info - создать ветку feature/add-branch-info и сразу начать работать в ней.
git checkout feature/add-branch-info - переключение на ветку feature/add-branch-info
git diff feature/add-branch-info bugfix/fix-branch - сравнить какие изменения произошли в fix-branch по отношению к add-branch-info
```
