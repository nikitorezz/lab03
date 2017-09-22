## Laboratory work III

Данная лабораторная работа посвещена изучению систем контроля версий на примере **Git**.

```bash
$ open https://git-scm.com
```

## Tasks

- [x] 1. Создать публичный репозиторий с названием **lab03** и с лиценцией **MIT**
- [x] 2. Ознакомиться со ссылками учебного материала
- [x] 3. Выполнить инструкцию учебного материала
- [x] 4. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial

```ShellSession
$ export GITHUB_USERNAME=nikitorezz
$ export GITHUB_EMAIL=nikitorezz@gmail.com
$ alias edit=vim
```
Инициализация директории для новой лабораторной работы
```ShellSession
$ mkdir lab03 && cd lab03  # создание директории lab03 и переход в неё
$ git init	# создание локального репозитория
$ git config --global user.name ${GITHUB_USERNAME}	# настройка рользовательских данных
$ git config --global user.email ${GITHUB_EMAIL}
$ git config -e --global
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab03 # добавление удаленного репозитория
$ git pull origin master	 # получение данных
$ touch README.md	 # создание README.md
$ git status 	# получение статуса файлов
$ git add README.md	# добавление файла в гит
$ git commit -m"added README.md"	# коммит README.md
$ git push origin master 	# пуш в репозиторий в master
```

Добавить на сервисе **GitHub** в репозитории **lab03** файл **.gitignore**
со следующем содержимом:

```ShellSession
*build*/
*install*/
*.swp
```
Получение изменений
```ShellSession
$ git pull origin master	 # получение данных
$ git log			# получение истории коммитов
```
Создание директорий для проекта
```ShellSession
$ mkdir sources       # создание директории для исходного кода заголовочных файлов и примеров
$ mkdir include				
$ mkdir examples      
```

Заполнение файла исходного кода
```ShellSession
$ cat > sources/print.cpp <<EOF		
#include <print.hpp>

void print(const std::string& text, std::ostream& out) {
  out << text;
}

void print(const std::string& text, std::ofstream& out) {
  out << text;
}
EOF                  
```
Заполнение заголовочного файла
```ShellSession
$ cat > include/print.hpp <<EOF
#include <string>
#include <fstream>
#include <iostream>

void print(const std::string& text, std::ostream& out = std::cout);
void print(const std::string& text, std::ofstream& out);
EOF              
```
Заполнение файла с примером 1
```ShellSession
$ cat > examples/example1.cpp <<EOF
#include <print.hpp>

int main(int argc, char** argv) {
  print("hello");
}
EOF               
```
Заполнение файла с примером 2
```ShellSession
$ cat > examples/example2.cpp <<EOF
#include <fstream>
#include <print.hpp>

int main(int argc, char** argv) {
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
EOF              
```
Редактирование README.md с помощью vim
```ShellSession
$ edit README.md		
```
Пуш изменений в репозиторий
```ShellSession
$ git status			# получение статуса файлов
$ git add .	
$ git commit -m"added sources"		# коммит файлов
$ git push origin master # пуш в ветку master
```

## Report

```ShellSession
$ cd ~/workspace/labs/
$ export LAB_NUMBER=03
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gistup -m "lab${LAB_NUMBER}"
```

## Links

- [GitHub](https://github.com)
- [Bitbucket](https://bitbucket.org)
- [Gitlab](https://about.gitlab.com)
- [LearnGitBranching](http://learngitbranching.js.org/)

```
Copyright (c) 2017 Братья Вершинины
```
