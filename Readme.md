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

## Перемещение между сохранениями

## Журнал изменений

## Ветки в Git

## Слияние веток и разрешение конфликтов

## Удаление веток