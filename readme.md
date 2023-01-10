# Инструкция по работе с Git

## Что такое Git ?
***Git*** - самая популярная реализация распределенной системы контроля версий (версионность поддерживается и на сервере, и  у каждого клиента). самрй распространенной реплизацией ***Git*** является (GitHub)[https://github.com]

## Подготовка репозитория
Для создания репозитория используется команда *git init*. Для этого необходимо открыть в терминале папку с будущем репозиторием и написать *git init*

### Добавление файлов к коммиту
Для добавления файла к новому коммиту используется команда *git add*. Используется она следующем образом: в терминале с папкой репозиторием пишем *git add <название файла>*.

### Создание коммита
Для создания новой фиусации коммита используется команда * git commit*. Для этого в терминале с папкой-репозиторием *git commit - m <сообщение к коммиту>*. Сообщение к коммиту писать ***ОБЯЗАТЕЛЬНО!!!***
## Журнал изменений 
Для просмотра историй изменений используется команда *git log*. Для этого в терминале с папкой-репозиторием необходимо написать *git log*.
## Перемещение между "сохранениями"
для перемещения на другую фиксацию(коммит) используется команда *git checkout*. Для этого  необходимо, как показано в прошло пункте, в журнале изменений найти необходимый коммит и его хеш (номер), после чего в терминале с папкой-репозиторием надо написать *git checkout <хеш коммита>*.После выполнения этой команды мы попадаем в состояние **detached head**, в котором никакие следующие комитты сохряняться не будут.  Для выхода из этого состояния необходимо писать *git checkout master*.

## Ветвление в Git 
### Создание веток в гит 
Для создания новой ветки используется команда *git branch*. Для этого в терминале с папкой репозиторием необходимо написать *git branch <название ветки>*

### Просмотр списка веток 
Для просмотра списка веток используется команда *git branch*. Для этого в терминале с папкой-репозиторием необходимо написать *git branch*.Выделенное зеленым со звездочкой ветка- это ветка, в данный момент на которой мы находимся 
### Перемещение между ветками 
Для перехода на другую ветку используется команда *git checkout*. Для этого в терминале с папкой-репозиторием необходимо написать *git checkout <название ветки>*. Такая ветка должна **существовать**

Под веткой принято понимать независимую последовательность коммитов в хронологическом порядке. Однако конкретно в Git реализация ветки выполнена как указатель на последний коммит в рассматриваемой ветке. После создания ветки уже новый указатель ссылается на текущий коммит.

Имя основной ветки Git-проекта по умолчанию — master (однако зачастую бывает main, например, в GitHub), она появляется сразу при инициализации репозитория. Эта ветка ничем не отличается от остальных и также ее можно переименовать, но по договоренности master принято считать главной веткой в проекте.

### Основной инструмент
Команда git branch — главный инструмент для работы с ветвлением. С ее помощью можно добавлять новые ветки, перечислять и переименовывать существующие и удалять их.
Чтобы в Git добавить ветку мы используем:

*$ git branch <name of new branch>*

После данной операции ветка уже была создана, но вы по-прежнему находитесь в прежней ветке. Если вы планируете переместиться на другую ветку, в том числе только что созданную, необходимо написать checkout:

*$ git checkout <name of branch>*
Для того чтобы определить, где сейчас находится разработчик, Git использует специальный указатель HEAD, ссылающийся на текущую локальную ветку. В результате checkout HEAD переместится на иную ветку.

## Слияние веток и cпособы решения конфликтов
Ветвление позволяет разделять рабочий процесс, оптимизировать тестирование и написание нового кода. Однако после того, как разработчик убедился, что написанный им кусок кода готов и его можно отправить к остальной части итоговой версии, удобно переместить его в основную ветку. Такой подход дает возможность получить к концу разработки проекта целый продукт в одном месте.
Для этого в Git предусмотрено слияние — перенос изменений с одной ветки на другую. Однако сливаемая ветка (под этим определением мы подразумеваем ветку, у которой берем изменения для «вливания» их в другую ветвь) никак не меняется и остается в прежнем состоянии. Такие преобразования мы получаем, применив git merge

*$ git merge <name of merged branch>*
Операция может привести к появлению конфликтов при попытке слить ветки. Это вызвано тем, что изменения удаляют или переписывают информацию в существующих файлах. При попытке некорректного слияния Git останавливает выполнение команды, чтобы вы могли разрешить конфликт.
Также стоит упомянуть о существовании ключей, предназначенных специально для работы с конфликтами:

 * abort — прерывает слияние и возвращает все к началу
 * continue — продолжает слияние после разрешения конфликта
Решить конфликт можно двумя способами:

Вручную разрешить файловый конфликт. Для этого нужно самим изменить файлы, с которыми возникли проблемы. Мы получим файлы такими, какими и представляли их при попытке слияния.
Выбрать более подходящий файл, а от второго отказаться.

## Удаление веток
Для корректного удаления нужно помнить несколько правил:

 * Нельзя удалить ветку, в которой вы находитесь. Git выкинет ошибку и не произведет удаление. Следовательно, нужно перейти на другую ветку.

 * Git не позволит удалить ветку, у которой есть несохраненные изменения. Так мы избегаем ситуации, когда часть написанного кода будет безвозвратно утеряна. Если же мы уверены, что изменения в этой версии не нужны и их можно смело удалять, то вместо флага -d используем -D:

        $ git branch -D <name of branch>

Соблюдая все условия, нам удастся удалить указанную ветвь.

## ВЫВОД
таким образо мы расммотрели следующие пункты работы в Git:
что такое гит, подготовка репозитория, создание коммитов, журнал изменений, перемещения, ветки их слияние и разрешение конфликтов, удаление веток.
