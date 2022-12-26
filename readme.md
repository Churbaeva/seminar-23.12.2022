# Инструкция по работе с Git

## Что такое Git ?
***Git*** - самая популярная реализация распределенной системы контроля версий (версионность поддерживается и на сервере, и  у каждого клиента). самрй распространенной реплизацией ***Git*** является (GitHub)[https://github.com]

## Подготовка репозитория
Для создания репозитория используется команда *git init*. Для этого необходимо открыть в терминале папку с будущем репозиторием и написать *git init*

## Создание коммитов


### Добавление файлов к коммиту
Для добавления файла к новому коммиту используется команда *git add*. Используется она следующем образом: в терминале с папкой репозиторием пишем *git add <название файла>*.

### Создание коммита
Для создания новой фиусации коммита используется команда * git commit*. Для этого в терминале с папкой-репозиторием *git commit - m <сообщение к коммиту>*. Сообщение к коммиту писать ***ОБЯЗАТЕЛЬНО!!!***
## Журнал изменений 
Для просмотра историй изменений используется команда *git log*. Для этого в терминале с папкой-репозиторием необходимо написать *git log*.
## Перемещение между "сохранениями"
для перемещения на другую фиксацию(коммит) используется команда *git checkout*. Для этого  необходимо, как показано в прошло пункте, в журнале изменений найти необходимый коммит и его хеш (номер), после чего в терминале с папкой-репозиторием надо написать *git checkout <хеш коммита>*.После выполнения этой команды мы попадаем в состояние **detached head**, в котором никакие следующие комитты сохряняться не будут.  Для выхода из этого состояния необходимо писать *git checkout master*.

## Ветки в Git 

## Слияние веток и разрещение конфликтов

## Удаление веток
Для корректного удаления нужно помнить несколько правил:

 * Нельзя удалить ветку, в которой вы находитесь. Git выкинет ошибку и не произведет удаление. Следовательно, нужно перейти на другую ветку.

 * Git не позволит удалить ветку, у которой есть несохраненные изменения. Так мы избегаем ситуации, когда часть написанного кода будет безвозвратно утеряна. Если же мы уверены, что изменения в этой версии не нужны и их можно смело удалять, то вместо флага -d используем -D:

        $ git branch -D <name of branch>

Соблюдая все условия, нам удастся удалить указанную ветвь.