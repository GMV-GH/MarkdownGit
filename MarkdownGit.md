# Основные команды для работы с Git и GitHub

## Создание репозитория
* ___git init___ Переместитесь в папку с проектом и выполните команду *git init*.
После исполнения команды появится сообщение об инициализации репозитория.
Оно означает, что Git начал отслеживать файлы проекта и будет записывать изменения в скрытую папку *.git*.

## Рабочий процесс
* ___git add___ Добавление файлов в индекс. Индекс - промежуточная зона перед репозиторием. 
После попадания в индекс файлы становятся подготовленными к коммиту (staged).
 Вариации команды:
    * *git add file_name* Добавляем в индекс один файл.
    * *git add file_name_1 file_name_2 file_name_3* Добавляем в индекс несколько файлов.
    * *git add .* добавляем в индекс все изменённые файлы; 
    * _git add *.js_ перенесёт в индекс все файлы из текущей папки с расширением .js

* ___git status___ проверка статуса репозитория. Показывает, какие неотслеживаемые файлы попали в проект, какие файлы находятся в индексе и какие сохранённые файлы вы изменили в репозитории.
* ___git commit___ добавление файлов в репозиторий. Вариации команды:
    + *-m* добавление сообщения коммита минуя текстовый редактор
    + *-a* создание нового коммита, минуя индекс. 
* ___git log___ просмотр журнала коммитов. Показывает историю коммитов в обратном хронологическом порядке.
Вариации команды:
    + *--oneline* расположение информации о каждом коммите в одну строку.
* ___git show___ просмотр коммита. Выводит информацию об одном коммите. Сообщение делится на два блока: часть с метаданными и список изменений, внесённых в коммит.
* ___git diff___ просмотр изменений до коммита. Показывает разницу между последним коммитом и текущим состоянием репозитория. То есть последний коммит сравнивается со всеми неотслеживаемыми файлами, которые ещё не переведены в индекс.
Вариации команды: 
    + *--staged* разница между последним коммитом и отслеживаемым состоянием репозитория.
    + *commit_hash* разница между последним коммитом и коммитом с указанным хешем.
    + *file_name* разница между последним коммитом и текущим состоянием файла.
* ___git restore___ отмена изменений. Возвращает файл к состоянию последнего коммита. Она отменяет все изменения, если файл не перенесён в индекс. Если файл попал в индекс, то вместе с названием команды нужно использовать опцию --staged.
Вариации команды:
    + *git restore file_name* вернуть неотслеживаемый файл к состоянию последнего коммита.
    + *git restore --staged* вернуть все файлы из индекса к состоянию последнего коммита.
    + *git restore --staged file_name* вернуть указанный файл из индекса к состоянию последнего коммита.
* ___git rm___ удаление файлов из индекса. Позволяет удалить файл, который по ошибке попал в индекс.
После выполнения команды файл пропадёт из индекса и из папки на вашем компьютере, в которой хранится проект.
Если вы хотите удалить файл только из индекса, то команду git rm нужно использовать вместе с опцией *--cached*.
* ___git reset___ откат коммита. Позволяет отменить любое количество сделанных коммитов и вернуть проект к какому-то состоянию в прошлом.
Вариации команды:
    + *git reset --soft commit_hash* проект откатывается к указанному коммиту и переводит все последующие коммиты в индекс. Вы можете сразу сделать новый коммит и перезаписать историю проекта, оставив исходные файлы без изменений.
    + *git reset --mixed commit_hash* откаченные файлы попадают в неотслеживаемую зону. Вы можете эти файлы изменить, удалить или вернуть обратно в индекс.
    + *git reset --hard commit_hash* проект откатывается к указанному коммиту и удаляет все последующие коммиты без возможности их восстановления.

## Ветвление
* ___git branch <branch_name>___ создание новой ветки. 
Вариации команды.
    + *git branch* Запрашиваем список всех доступных веток.
    + *git branch <branch_name>* создание новой ветки.
    + *git branch -m old_branch_name new_branch_name* переименование ветки.
    + *git branch -d <branch_name>* удаление ветки.
* ___git checkout___ переключение между ветками. 
Вариации команды.
    + *git checkout -b branch_name* создание новой ветки и переход в неё одной командой.
    + *git switch branch_name* переход на новую ветку. Команда не срабатывает, если переход на выбранную ветку может привести к потере данных.
* ___git merge___ слияние репозиториев. Позволяет добавить изменения из одной ветки в другую.
Вариации команды.
    + *git merge secondary_branch* Сливаем изменения из второстепенной ветки в основную.

## Удалённый репозиторий
* ___git remote___ привязка локального и удалённого репозитория
Вариации команды.
    + *git remote add origin git@github.com:ваш_профиль/ваш_репозиторий.git* привязка локального репозитория к удалённому на GitHub
    + *git remote* просмотр удалённых репозиториев.
    + *git remote — v* просмотр удалённых URL-адресов
* ___git push___ отправка изменений в удалённый репозиторий.
Вариации команды.
    + *git push -u origin main* Команда для первой загрузки изменений в удалённый репозиторий: текущая ветка будет связана
     с веткой main в удалённом репозитории origin.
    + *git push* Команда для второй и последующих загрузок изменений в удалённый репозиторий.
* ___git pull___ получение изменений из удалённого репозитория. 
* ___git clone URL___ Выполняет копирование удаленного репозитория в локальный.