<-- [Назад](../readme.md)

---

# Создание Git-репозитория

Обычно вы получаете репозиторий Git одним из двух способов: 
- Вы можете взять локальный каталог, который в настоящее время не находится под версионным контролем, и превратить его в репозиторий Git, либо 
- Вы можете ***клонировать*** существующий репозиторий Git из любого места.

В обоих случаях вы получите готовый к работе Git репозиторий на вашем компьютере.

## Создание репозитория в существующем каталоге

Если у вас уже есть проект в каталоге, который не находится под версионным контролем Git, то для начала нужно перейти в него. Если вы не делали этого раньше, то для разных операционных систем это выглядит по-разному:

для Linux:
```bash
$ cd /home/user/my_project
```
для macOS:
```bash
$ cd /Users/user/my_project
```
для Windows:
```bash
$ cd C:/Users/user/my_project
```
а затем выполните команду:
```bash
$ git init
```
Эта команда создаёт в текущем каталоге новый подкаталог с именем .git, содержащий все необходимые файлы репозитория — структуру Git репозитория. На этом этапе ваш проект ещё не находится под версионным контролем.

Если вы хотите добавить под версионный контроль существующие файлы (в отличие от пустого каталога), вам стоит добавить их в индекс и осуществить первый коммит изменений. Добиться этого вы сможете запустив команду `git add` несколько раз, указав индексируемые файлы, а затем выполнив `git commit`:
```bash
$ git add *.c
$ git add LICENSE
$ git commit -m 'Initial project version'
```
Теперь у вас есть Git-репозиторий с отслеживаемыми файлами и начальным коммитом.
## Клонирование существующего репозитория

Клонирование репозитория осуществляется командой `git clone <url>`. Например, если вы хотите клонировать библиотеку libgit2, вы можете сделать это следующим образом:
```bash
$ git clone https://github.com/libgit2/libgit2
```
Эта команда создаёт каталог libgit2, инициализирует в нём подкаталог .git, скачивает все данные для этого репозитория и извлекает рабочую копию последней версии. Если вы перейдёте в только что созданный каталог libgit2, то увидите в нём файлы проекта, готовые для работы или использования. Для того, чтобы клонировать репозиторий в каталог с именем, отличающимся от libgit2, необходимо указать желаемое имя, как параметр командной строки:
```bash
$ git clone https://github.com/libgit2/libgit2 mylibgit
```
Эта команда делает всё то же самое, что и предыдущая, только результирующий каталог будет назван mylibgit.

---

<-- [Назад](../readme.md)
