<-- [Назад](../readme.md)

---

# Очистка рабочего каталога

Наконец, у вас может возникнуть желание не прятать некоторые из изменений или файлов в вашем рабочем каталоге, а просто избавиться от них. Команда git clean сделает это для вас.

Одной из распространённых причин для этого может быть удаление мусора, который был сгенерирован при слиянии или внешними утилитами, или удаление артефактов сборки в процессе её очистки.



Предположим, вы хотите удалить мусор и очистить ваш рабочий каталог; вы можете сделать это с помощью `git clean`. Для удаления всех неотслеживаемых файлов в вашем рабочем каталоге, вы можете выполнить команду `git clean -f -d`, которая удалит все файлы и также все каталоги, которые в результате станут пустыми. Параметр `-f` (сокращение от слова *force* — заставить) означает принудительное удаление, подчеркивая, что вы действительно хотите это сделать, и требуется, если переменная конфигурации Git *clean.requireForce* явным образом не установлена в *false*.

Если вы хотите только посмотреть, что будет сделано, вы можете запустить команду с опцией `-n`, которая означает «имитируй работу команды и скажи мне, что ты будешь удалять».
```bash
$ git clean -d -n
Would remove test.o
Would remove tmp/
```
По умолчанию команда `git clean` будет удалять только неотслеживаемые файлы, которые не добавлены в список игнорируемых. Любой файл, который соответствует шаблону в вашем .gitignore, или другие игнорируемые файлы не будут удалены. Если вы хотите удалить и эти файлы (например, удалить все .o-файлы, генерируемые в процессе сборки, и таким образом полностью очистить сборку), вы можете передать команде очистки опцию `-x`.
```bash
$ git status -s
 M lib/simplegit.rb
?? build.TMP
?? tmp/

$ git clean -n -d
Would remove build.TMP
Would remove tmp/

$ git clean -n -d -x
Would remove build.TMP
Would remove test.o
Would remove tmp/
```
Если вы не знаете, что сделает при запуске команда `git clean`, всегда сначала выполняйте её с опцией `-n`, чтобы проверить дважды, перед заменой `-n` на `-f` и выполнением настоящей очистки. Другой способ, который позволяет вам более тщательно контролировать сам процесс — это выполнение команды с опцией `-i` (в «интерактивном» режиме).

Вам нужно быть очень аккуратными с этой командой, так как она предназначена для удаления неотслеживаемых файлов из вашего рабочего каталога. Даже если вы передумаете, очень часто нельзя восстановить содержимое таких файлов. Более безопасным вариантом является использование команды [git stash](./stash.md "git stash") `--all` для удаления всего, но с сохранением этого в виде припрятанных изменений.

---

<-- [Назад](../readme.md)