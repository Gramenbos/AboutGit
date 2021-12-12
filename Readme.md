# Инструкция по работе с Git

## Что такое Git?

Git - одна из реализаций распределенных систем контроля версий, имеющая как локальную версионность, так и версионность на сервере. Git является самой популярной системой контроля версий на сегодняшний день.

## Подготовка репозитория
Для того, чтобы создать репозиторий в указанной папке, использкуется команда *git init*. Для этого достаточно написать команду *git init* в папке с будущим репозиторием.

## Создание фиксаций

### Просмотр информации об изменениях

Для того, чтобы просмотреть информацию об изменениях, сделанных в текущей ветке, необходимо использовать команду *git status*. Для этого достаточно ипользовать *git status* в папке с репозиторием.

### Добавление файла к коммиту
Для того, чтобы добавить файл к новому коммиту ("сохранению"), необходимо использовать команду *git add*. Используется она следующим образом: в папке с репозиторием пишем команду *git add <имя файла>*

### Создание коммитов

Для создания новой фиксации необходимо использовать команду *git commit*. Используется она следующим образом: в папке с репозиторием пишется команда *git commit -m "<сообщение к коммиту>"*. Все файлы коммита должны быть предварительно добавлены с помощью команды *git add*. Сообщение к коммиту писать ***ОБЯЗАТЕЛЬНО***.

## Журнал изменений

Для просмотра журнала изменений (событий) необходимо использовать команду *git log*. Будет показан журнал всех изменений (коммитов), с указанием номера (id) коммита, его автора, e-mail автора, даты и времени создания коммита, а также комментария к коммиту. Например:
>commit 9aa9532330a1c0dac292f5db12431e8aff13c13e
>Author: Evgeniy Murzanaev <gramenbos@gmail.com>
>
>Date:   Sat Dec 11 22:50:57 2021 +0300
>
>Created file ForExample

Кроме того, если после команды *git log* добавить параметр *--graph*, то журнал изменений будет изображен с добавлением графических элементов, для более наглядной демонстрации веток.

## Перемещение между сохранениями

Чтобы перемещаться между различными сохранениями (коммитами), необходимо ввести команду *git checkout <id коммита>*, например:
> git checkout 73e9d88333e66a0c23d5141eb57f542f0e096865

При этом достаточно указать первые 5-6 знаков номера коммита, наприме:
> git checkout 73e9d

Чтобы вернуться к последнему коммиту, достаточно ввести команду *git checkout master*.

## Ветки в Git

Git, как система контроля версий, поддерживает ветвление. Используя ветвление, Вы отклоняетесь от основной линии разработки и продолжаете работу независимо от неё, не вмешиваясь в основную линию. 

### Создание веток

Чтобы создать ветку, необходимо использовать команду *git branch mew_branch_name*, например:
> git branch NewBranch

Обращаем внимание, что эта команда только создает новую ветку, не переходя в нее. 

### Переход между ветками

Для перехода используется команда *git checkout branch_name* (по аналогии с переходом между коммитами), например:
> git checkout NewBranch

Для возвращения в основную ветку, необходимо ввести команду
> git checkout master

### Просмотр списка веток

Для просмотра списка всех веток, с указанием, какая из них является текущей, используется команда *git branch*. Текущая ветка будет подсвечена зеленым цветом и отмечена звездочкой (*).

### Слияние веток и разрешение конфликтов

Для слияния (объединения) веток используется команда *git merge BranchName*. 
>**ВНИМАНИЕ:** команду необходимо вводить из той ветки, с которой хотим выполнить слияние, а указывать в команде имя той ветки, которую вы хотите добавить (влить) в текущую.

После выполнения этой команды возможны два исхода:
1. Слияние прошло успешно, и мы получили файл, в котором есть данные из обоих веток (дополнили файл информацией из другой ветки). В таком случае коммит создается автоматически.
2. Слияние произошло с ***конфликтом***. Это возможно в случае, если одни и те же строки в файле были изменены в обоих ветках, и программа не понимает, какие из них надо оставить, а какие - нет.
   
Возможное отображение конфликта в терминале:
>CONFLICT (content): Merge conflict in README.md
>
>Automatic merge failed; fix conflicts and then commit the result.

Git не создал коммит слияния автоматически. Он остановил процесс до тех пор, пока вы не разрешите конфликт.

В конфликтующие файлы Git добавляет специальные маркеры конфликтов, чтобы вы могли исправить их вручную. Кроме того, они наглядно подсвечиваются разными цветами.

Для быстрого разрешения конфликта можно использовать появившиеся ссылки:
- Accept Current Change (оставить как в текущей ветке)
- Accept Incoming Change (оставить как в ветке, которую сливаем с текущей)
- Accept Both Changes (оставить все изменения)
- Compare Changes (сравнить изменения)

В любом случае всегда можно отредактировать файл вручную.
>**ВНИМАНИЕ:** после слияния с конфликтом коммит автоматически не создается, поэтому после разрешения конфликта необходимо сделать коммит.

### Удаление веток

После слияния веток обычно надобность ветки, которая была слита с главной, отпадает. И её можно удалить. Конечно, удалить ветку можно в любом случае, если она не нужна.
Для удаления ветки используется команда *git branch* с параметром *-d*, например:
> git branch -d BranchName

Указанной командой можно удалить ветку, к которой была применена команда *merge*, то есть данные из удаляемой ветки были добавлены в главную.
При необходимости удалить ветку без ее слияния, используется та же команда, но с большой буквой *D*:
> git branch -D BranchName


### Вот мы изучили основы Git. Спасибо за внимание!
