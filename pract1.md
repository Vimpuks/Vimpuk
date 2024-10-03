# Практическое занятие №1. Введение, основы работы в командной строке

В.С. Карамышева, РТУ МИРЭА

Научиться выполнять простые действия с файлами и каталогами в Linux из командной строки. Сравнить работу в командной строке Windows и Linux.

## Задача 1

Вывести отсортированный в алфавитном порядке список имен пользователей в файле passwd (вам понадобится grep).
```
grep '.*' /etc/passwd | cut -d: -f1 | sort
```
![photo_5469761901270523833_y](https://github.com/user-attachments/assets/53bf632e-ebf2-47b3-b2ff-368c05872721)

## Задача 2

Вывести данные /etc/protocols в отформатированном и отсортированном порядке для 5 наибольших портов, как показано в примере ниже:

```
awk '{print $2, $1}' /etc/protocols | sort -nr | head -n 5
```
![d6682125-0cda-4e2f-b8a0-3a93ca1b44be](https://github.com/user-attachments/assets/410b36ca-8d21-4900-b2ec-06abea358ec0)

## Задача 3

Написать программу banner средствами bash для вывода текстов, как в следующем примере (размер баннера должен меняться!):

```
#!/bin/bash

text=$*
length=${#text}

for i in $(seq 1 $((length + 2))); do
    line+="-"
done

echo "+${line}+"
echo "| ${text} |"
echo "+${line}+"
```
![photo_5469761901270523883_y](https://github.com/user-attachments/assets/a385fd0a-b0c6-4293-8dfa-bed56b6b2c63)

Перед отправкой решения проверьте его в ShellCheck на предупреждения.

## Задача 4

Написать программу для вывода всех идентификаторов (по правилам C/C++ или Java) в файле (без повторений).

Пример для hello.c:

```
#!/bin/bash

file="$1"

id=$(grep -o -E '\b[a-zA-Z]*\b' "$file" | sort -u)
_________________________________

grep -oE '\b[a-zA-Z_][a-zA-Z0-9_]*\b' hello.c | grep -vE '\b(int|void|return|if|else|for|while|include|stdio)\b' | sort | uniq

```
![image](https://github.com/user-attachments/assets/c700966d-187e-43cd-89d8-37cadfcf9f6c)

## Задача 5

Написать программу для регистрации пользовательской команды (правильные права доступа и копирование в /usr/local/bin).

Например, пусть программа называется reg:

```
#!/bin/bash

file=$1

chmod 755 "./$file"

sudo cp "$file" /usr/local/bin/
```
![image](https://github.com/user-attachments/assets/648c2724-b1e8-4272-9aae-f1487f9b2969)

В результате для banner задаются правильные права доступа и сам banner копируется в /usr/local/bin.

