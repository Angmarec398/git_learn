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
git rm --cached config.py - Убрать файл из отслеживания Git
git status - Статус файлов

git filter-branch --force --index-filter \ 'git rm --cached --ignore-unmatch app.py' \ --prune-empty --tag-name-filter cat -- --all  - Удалить файл из всех коммитов (пример app.py)

rm -rf .git - рассоединиться с Git
	ssh-keygen -t ed25519 -C test@gmail.com - создание SSH ключа для аккаунта test@gmail.com

git commit --amend -m "Test write Readme and add ambed.txt" - редактирование текста последнего коммита
git commit --amend --no-edit - Добавление файла/файлов добавленных через git add - в последний коммит, без создания нового коммита.

git reset --hard 4987153   - откатить изменения до коммита 4987153

git restore --staged .\example.txt - убрать файл example.txt из очереди на сохранение (git add example.txt)
git restore .\example.txt - откатит файл до последней версии сохраненной при помощи git add и git commit

```