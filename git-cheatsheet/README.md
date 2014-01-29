# Git для начинающих.

## Начало работы
### Создание ssh ключа

Переходите по [ссылке](https://help.github.com/articles/generating-ssh-keys) и читайте.

### Регистрация имени и почты в git
Для этого потребуется ввести в консоль следующие команды:

`git config --global user.name "ваше имя"`  

`git config --global user.email "ваша почта"`

Если вы собираетесь начать использовать Git для существующего проекта, то вам необходимо перейти в каталог проекта c помощью команды 

`cd ~/project/`


#### Установка значений по умолчанию

Приведенные значения позволяют раскрасить вывод git и сделать его более читаемым.

```bash
git config --global color.branch auto
git config --global color.diff auto
git config --global color.status auto
git config --global color.ui auto
```

### Создание репозитория

Репозиторий - это такое место, где вы можете хранить и изменять файлы.

В проектном каталоге нужно ввести команду

`git init`

Эта команда создаёт в текущем каталоге новый подкаталог с именем .git содержащий все необходимые файлы репозитория — основу Git-репозитория. На этом этапе 
ваш проект ещё не находится под версионным контролем. (В [главе 9](http://git-scm.com/book/ru/Git-%D0%B8%D0%B7%D0%BD%D1%83%D1%82%D1%80%D0%B8) приведено
подробное описание файлов содержащихся в только что созданном вами каталоге .git)

Если вы хотите включить некоторые файлы в версионный контроль git, то вам понадобится команда 

`git add /путь/к/файлу`  

Для того чтобы зафиксировать измененя в git, нужно ввести команду 

`git commit`

В фиксации изменений заключается весь смысл git. Фиксация изменений позволяет видеть кто и когда изменил какой-либо файл.

Для данной команды существуют несколько опций:

`-a` - опция для автоматического добавления файла при его коммите.  
`-m "сообщение коммита"` - опция для автоматического комментированя изменений файла при его коммите.  
`--amned` - откат изменений в файле.

Далее нам понадобится загрузить репозиторий в http://github.com. Но для начала нужно указать в какой репозиторий нужно загружать контент.
Для этого используется команда 

`git remote add git@github.com:soda-io/git-cheatsheet.git`

Далее осталось только загрузить контент в репозиторий http://github.com 

`git push -u origin master`

ждем пока файлы загрузятся на сервер.
Вот и все.

### Клонирование репозитория

Клонирование - это полное скачивание всех файлов из репозитория или гиста.

К примеру

`git clone git@github.com:soda-io/git-cheatsheet.git`

### Получения новых данных из репозитория

Означает скопировать данные из репозитория и переместить их в буфер обмена git

`git pull`

В дальнейшем можно вставить их в какой-либо другой репозиторий с помощью команды 

`git push`

## Ветки

Ветки представляют собой параллельные копии кода, которые поддерживаются за счет git. При создании репозитория создается одна ветка `master`. Посмотреть ветки репозитория можно с помощью команды

  ```bash
  git branch
  ```
  
Активная ветка будет помечена `*`.

Имена веток состоят из английских строчных букв, цифр и знака минус. 
Первый символ имени ветки должен быть английской буквой.
  
### Создание новой ветки


  ```bash
	git checkout -b BRANCH-NAME
  ```

После создания новой ветки (`BRANCH-NAME`) репозиторий автоматически переключается на нее. Все новые коммиты будут сохраняться в новой ветке. Для того чтобы перенести данные в другую ветку используется слияние веток.

### Переход между ветками

  ```bash
    git checkout NEW-BRANCH
  ```

Переход с активной ветки на `NEW-BRANCH` сопровождается восстановлением состояния ветки `NEW-BRANCH`. При этом все более поздние коммиты будут отменены, а вновь добавленые файлы удалены (они останутся в той ветке из которой был осуществлен переход).


### Слияние веток

Слияние - это автоматическое объединение кода в ветках.

 ```bash
 git merge OTHER-BRANCH
 ```
 
При объединении новые версии файлов замещают старые, удаленные файлы удаляются из активной ветки, а добавленные - добавляются.

В некоторых случаях, когда файл (или несколько) содержит конфликтующие коммиты, автоматическое слияние не происходит, а выдается сообщение об ошибке. Конфликтующие коммиты добавляются `git`ом в соответствующий файл. Для разрешения ситуации необходимо вручную отредактировать конфликтный файл, сохранить его и сделать коммит. 


