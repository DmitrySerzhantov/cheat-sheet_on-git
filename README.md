# cheat-sheet_on-git
# Шпаргалка по git :robot:

## Навигация
* **pwd** (от англ. print working directory, «показать рабочую папку») — покажи, в какой я папке;
* **ls** (от англ. list directory contents, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;
* **ls -a** — покажи также скрытые файлы и папки, названия которых начинаются с символа .;
* **cd first-project** (от англ. change directory, «сменить директорию») — перейди в папку first-project;
* **cd first-project/html** — перейди в папку html, которая находится в папке first-project;
* **cd ..** — перейди на уровень выше, в родительскую папку;
* **cd ~ —** перейди в домашнюю директорию (/Users/Username);
* **cd /** — перейди в корневую директорию.

## Работа с файлами и папками
#### Создание
* **touch index.html**(англ. touch, «коснуться») — создай файл index.html в текущей папке;
* **touch index.html style.css script.js** — если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел;
* **mkdir second-project** (от англ. make directory, «создать директорию») — создай папку с именем second-project в текущей папке.
#### Копирование и перемещение
* **cp file.txt ~/my-dir** (от англ. copy, «копировать») — скопируй файл в другое место;
* **mv file.txt ~/my-dir** (от англ. move, «переместить») — перемести файл или папку в другое место.
### Чтение
* **cat file.txt** (от англ. concatenate and print, «объединить и распечатать») — распечатай содержимое текстового файла file.txt.
### Удаление
* **rm about.html** (от англ. remove, «удалить») — удали файл about.html;
* **rmdir images** (от англ. remove directory, «удалить директорию») — удали папку images;
* **rm -r second-project** (от англ. remove, «удалить» + recursive, «рекурсивный») — удали папку second-project и всё, что она содержит.
##Полезные возможности
Команды необязательно печатать и выполнять по очереди. Можно указать их списком — разделить двумя амперсандами **(&&).**
У консоли есть собственная память — буфер с несколькими последними командами. По ним можно перемещаться с помощью клавиш со стрелками вверх **(↑)** и вниз **(↓)**.
Чтобы не вводить название файла или папки полностью, можно набрать первые символы имени и дважды нажать **Tab**. Если файл или папка есть в текущей директории, командная строка допишет путь сама.
Например, вы находитесь в папке dev. Начните вводить cd first и дважды нажмите **Tab**. Если папка first-project есть внутри dev, командная строка автоматически подставит её имя. Останется только нажать **Enter.**

# Хеш — идентификатор коммита
* **Git** преобразует информацию о коммитах с помощью алгоритма SHA-1 и для каждого из них рассчитывает уникальный идентификатор — хеш.
* **Хеш** — основной идентификатор коммита и позволяет узнать его автора, дату и содержимое закоммиченных файлов.
Все хеши, а также таблицу соответствий хеш → информация о коммите Git хранит в папке .git.

# Элементы описания коммита
После вызова **git log** появляется список коммитов.

* Разберём элементы, из которых состоит описание:
строка из цифр и латинских букв после слова **commit** — это хеш коммита;
**Author** — имя автора и его электронная почта;
**Date** — дата и время создания коммита;
в конце находится сообщение коммита.

* Можно вызвать не только полный лог, но и сокращённый — это делается командой **git log --oneline**.
В сокращённом логе выводятся сокращённые хеши — их можно использовать точно так же, как и полные.

#HEAD
* При вызове команды git log вы также могли заметить надпись (HEAD -> master) после хеша одного из коммитов. В этом уроке расскажем, что она означает.

### Файл HEAD
* Файл HEAD (англ. «голова», «головной») — один из служебных файлов папки .git. Он указывает на коммит, который сделан последним (то есть на самый новый).
В этом можно убедиться с помощью терминала. Перейдите в папку .git командой cd. Посмотрите содержимое файла HEAD командой cat.

* В числе прочих файлов в папке .git есть служебный файл HEAD. Он указывает на самый свежий коммит.
Вместо хеша последнего коммита можно написать слово HEAD — Git вас поймёт.

# Статусы файлов в Git
* Статусы untracked/tracked, staged и modified
Одна из ключевых задач Git — отслеживать изменения файлов в репозитории. Для этого каждый файл помечается каким-либо статусом. Рассмотрим основные.
untracked (англ. «неотслеживаемый»)

* Мы говорили, что новые файлы в Git-репозитории помечаются как untracked, то есть неотслеживаемые. Git «видит», что такой файл существует, но не следит за изменениями в нём. У untracked-файла нет предыдущих версий, зафиксированных в коммитах или через команду **git add**.
staged (англ. «подготовленный»)
  * После выполнения команды **git add** файл попадает в staging area (от англ. stage — «сцена», «этап [процесса]» и area — «область»), то есть в список файлов, которые войдут в коммит. В этот момент файл находится в состоянии staged.
  В одном из предыдущих уроков мы сравнили коммит с фотографией. Можно развить эту аналогию и сказать, что команда **git add** добавляет персонажей (текущее содержимое файла или нескольких файлов) на сцену (англ. stage) для общей фотографии, а git commit делает снимок всей сцены целиком. 
💡 Staging area, index и cache
Staging area также называют index (англ. «каталог») или cache (англ. «кеш»), а состояние файла staged иногда называют indexed или cached.
Все три варианта могут встречаться в документации и в качестве флагов команд Git. А также в интернете — например, в вопросах и ответах на сайте Stack Overflow.

**tracked** (англ. «отслеживаемый»)

* Состояние **tracked** — это противоположность **untracked**. Оно довольно широкое по смыслу: в него попадают файлы, которые уже были зафиксированы с помощью **git commit**, а также файлы, которые были добавлены в staging area командой **git add**. То есть все файлы, в которых Git так или иначе отслеживает изменения.
**modified** (англ. «изменённый»)

Состояние **modified** означает, что Git сравнил содержимое файла с последней сохранённой версией и нашёл отличия. Например, файл был закоммичен и после этого изменён.
💡 Для файлов в состояниях staged и **modified** обычно не указывают, что они также tracked, потому что это состояние подразумевается.
Про **staged** и **modified**
* Команда git add добавляет в staging area только текущее содержимое файла. Если вы, например, сделаете git add file.txt, а затем измените file.txt, то новое содержимое файла не будет находиться в staging.
Git сообщит об этом с помощью статуса modified: файл изменён относительно той версии, которая уже в staging. Чтобы добавить в staging последнюю версию, нужно выполнить **git add file.txt** ещё раз.

* Статусом **untracked** помечается файл, о существовании которого Git знает, но не следит за изменениями в нём. Этот статус — противоположность tracked, в который попадают все файлы, отслеживаемые Git.
* Файл переходит в статус **staged** после выполнения **git add**.
* Статус **modified** означает, что файл был изменён.
Большинство файлов в проектах «шагает» по следующему циклу: «изменён» → «добавлен в список на коммит» → «закоммичен» → «изменён» → и так далее.

# Как читать git status
## Какие состояния показывает git status
* Большинство файлов в типичном проекте будут находиться в состоянии **tracked** (то есть закоммичены и не изменены после коммита). Вы не увидите это состояние в выводе команды **git status** — иначе она бы каждый раз выводила список вообще всех файлов проекта.
* В итоге **git status** показывает только следующие состояния файлов:
**staged** (Changes to be committed в выводе git status);
**modified** (Changes not staged for commit);
**untracked** (Untracked files).

# Команда git status 
* Всегда подскажет, что происходит с файлом: например, он добавлен в список «на коммит» или ещё вообще не отслеживается, или изменён.
**git status** показывает явно следующие состояния файлов: **untracked**, **staged** и **modified**.
**git status** подсказывает, какие команды можно выполнить, чтобы поменять состояние файла.

# Оформление сообщений к коммитам
#### Зачем вообще писать сообщения
* У каждого коммита в Git есть сообщение — то, что передаётся после параметра -m. Например: git commit -m "Добавить урок про оформление сообщений коммитов".
* Сообщения коммитов можно сравнить с надписями на коробках в кладовке. Если надписей нет, то нужную коробку будет сложно найти: придётся заглянуть в каждую, чтобы понять, что там. А если надписи есть, то нужная найдётся сразу.
* Как и надпись на коробке, сообщение коммита должно помочь определить, что внутри. Например, надпись на коробке «всякое разное» не очень полезная. Сообщение коммита «небольшие исправления» тоже: непонятно, что было исправлено в таком коммите и зачем.
* Есть общие рекомендации по тому, как правильно составить сообщение. Оно должно быть:
относительно коротким, чтобы его было легко прочитать;
информативным.
* Вот пример полезного сообщения в репозитории новостного сайта: Исправление опечатки в заголовке главной страницы на хорватском. Такое сообщение даёт много информации:
Исправление опечатки значит, что исправлена ошибка, которая была допущена при наборе. Такое исправление не меняет смысл. То есть, например, главному редактору не нужно перепроверять этот заголовок.
На хорватском говорит о том, что переводчикам на другие языки этот коммит можно смело пропускать.
В заголовке главной страницы указывает, где произошли изменения. Если, например, кто-то зайдёт на сайт и ему не понравится новый заголовок, он легко найдёт по истории (git log) автора этого коммита и спросит у него, почему заголовок теперь такой.
Пример плохого сообщения для того же коммита: Исправлена опечатка. Это сообщение даёт мало информации. В такой коммит придётся «заглядывать» — разбираться, что именно поменялось и зачем.

## Стили оформления

### Корпоративный
* Во многих компаниях применяется Jira — система для организации проектов и задач. У каждой задачи в Jira есть идентификатор из нескольких заглавных латинских букв и номера. Например, LGS-239 значит, что это 
239
* 239-я задача в проекте LGS (сокращение от англ. logistics — «логистика»).
В корпоративном стиле в начале сообщения обычно указывают Jira-ID, а после — текст сообщения.
**$ git commit -m "LGS-239: Дополнить список пасхалок новыми числами"**
Какие-то команды могут договариваться, с какой части речи начинать сообщение и какой длины оно должно быть, какие-то — нет. Но требование о наличии Jira-ID обычно строгое: оно позволяет автоматически связывать коммиты с задачами и проектами.
Conventional Commits

## Стандарт Conventional Commits (англ. «соглашение о коммитах»)
 отличается качественной документацией и подробной проработкой. Он подходит для репозиториев с исходным кодом программ. Использовать его для других типов проектов (например, для перевода книги) было бы неудобно.
Conventional Commits предлагает такой формат коммита: <type>: <сообщение>. Первая часть type — это тип изменений. Таких типов достаточно много. Вот два примера:
feat (англ. «навык») — для новой функциональности;
fix (от англ. «исправить», «устранить») — для исправленных ошибок.
Более подробный список можно увидеть на сайте с описанием этого стиля.
Например, сообщение может быть таким.
git commit -m "feat: добавить подсчёт суммы заказов за неделю" 
## GitHub-стиль
GitHub можно использовать не только для хранения файлов проекта, но и для ведения списка задач (англ. issue) этого проекта. Если коммит «закрывает» или «решает» какую-то задачу, то в его сообщении удобно указывать ссылку на неё. Для этого в любом месте сообщения нужно указать #<номер задачи>. Например, вот так.
$ git commit -m "Исправить #334, добавить график температуры" 
В таком случае GitHub свяжет коммит и задачу.
###Хорошо, когда:
* сообщение коммита легко читается;
 * оно информативное;
 * все сообщения оформлены в одном стиле.

 ### Инициализация репозитория
**git init** (от англ. initialize, «инициализировать») — инициализируй репозиторий.
Синхронизация локального и удалённого репозиториев
**git remote add origin** https://github.com/YandexPracticum/first-project.git (от англ. remote, «удалённый» + add, «добавить») — привяжи локальный репозиторий к удалённому с URL https://github.com/YandexPracticum/first-project.git;
**git remote -v**(от англ. verbose, «подробный») — проверь, что репозитории действительно связались;
**git push -u origin main**(от англ. push, «толкать») — в первый раз загрузи все коммиты из локального репозитория в удалённый с названием origin.
💡 Ваша ветка может называться master, а не main. Подправьте команду, если это необходимо.
**git push** (от англ. push, «толкать») — загрузи коммиты в удалённый репозиторий после того, как он был привязан с помощью флага -u.
Подготовка файла к коммиту
**git add todo.txt** (от англ. add, «добавить») — подготовь файл todo.txt к коммиту;
**git add --all** (от англ. add, «добавить» + all, «всё») — подготовь к коммиту сразу все файлы, в которых были изменения, и все новые файлы;
**git add .** — подготовь к коммиту текущую папку и все файлы в ней.
Создание и публикация коммита
git commit -m "Комментарий к коммиту." (от англ. commit, «совершать», фиксировать» + message, «сообщение») — сделай коммит и оставь комментарий, чтобы было проще понять, какие изменения сделаны;
**git push** (от англ. push, «толкать») — добавь изменения в удалённый репозиторий.
Просмотр информации о коммитах
**git log** (от англ. log, «журнал [записей]») — выведи подробную историю коммитов;
**git log --oneline** (от англ. log, «журнал [записей]» + oneline, «одной строкой») — покажи краткую информацию о коммитах: сокращённый хеш и сообщение.
Просмотр состояния файлов
**git status** (от англ. status, «статус», «состояние») — покажи текущее состояние репозитория.
Добавление изменений в последний коммит
**git commit --amend --no-edit** (от англ. amend, «исправить») — добавь изменения к последнему коммиту и оставь сообщение прежним;
**git commit --amend -m** "Новое сообщение" — измени сообщение к последнему коммиту на Новое сообщение.
💡 Выйти из редактора Vim: нажать Esc, ввести :qa!, нажать Enter.
«Откат» файлов и коммитов
**git restore --staged hello.txt** (от англ. restore, «восстановить») — переведи файл hello.txt из состояния staged обратно в untracked или modified;
**git restore hello.txt** — верни файл hello.txt к последней версии, которая была сохранена через git commit или git add;
**git reset --hard b576d89** (от англ. reset, «сброс», «обнуление» + hard, «суровый») — удали все незакоммиченные изменения из staging и «рабочей зоны» вплоть до указанного коммита.
Просмотр изменений
**git diff** (от англ. difference, «отличие», «разница») — покажи изменения в «рабочей зоне», то есть в modified-файлах;
**git diff a9928ab 11bada1** — выведи разницу между двумя коммитами;
**git diff --staged** — покажи изменения, которые добавлены в staged-файлах.
## Работа с ветками

**git clone** git@github.com:YandexPraktikum/first-project.git (от англ. clone, «клон», «копия») — склонируй репозиторий с URL first-project.git из аккаунта YandexPraktikum на мой локальный компьютер.
### Создание веток
**git branch** feature/the-finest-branch (от англ. branch, «ветка») — создай ветку от текущей с названием feature/the-finest-branch;
**git checkout -b** feature/the-finest-branch — создай ветку feature/the-finest-branch и сразу переключись на неё.
Навигация по веткам
git branch (от англ. branch, «ветка») — покажи, какие есть ветки в репозитории и в какой из них я нахожусь (текущая ветка будет отмечена символом *);
git checkout feature/br — переключись на ветку feature/br.
### Сравнение веток
git diff main HEAD (от англ. difference, «отличие», «разница») — покажи разницу между веткой main и указателем на HEAD;
git diff HEAD~2 HEAD — покажи разницу между тем коммитом, который был два коммита назад, и текущим.
### Удаление веток
git branch -d br-name — удали ветку br-name, но только если она является частью main;
git branch -D br-name — удали ветку br-name, даже если она не объединена с main.
### Слияние веток
git merge main (от англ. merge, «сливать», «поглощать») — объедини ветку main с текущей активной веткой. 
Работа с удалённым репозиторием
git push -u origin my-branch (от англ. push, «толкнуть», «протолкнуть») — отправь новую ветку my-branch в удалённый репозиторий и свяжи локальную ветку с удалённой, чтобы при дополнительных коммитах можно было писать просто git push без -u;
git push my-branch — отправь дополнительные изменения в ветку my-branch, которая уже существует в удалённом репозитории;
git pull (от англ. pull, «вытянуть») — подтяни изменения текущей ветки из удалённого репозитория.