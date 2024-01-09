# [Levels here](https://overthewire.org/wargames/bandit/)

We will be using 'sshpass -p _password_' to enter the password directly from the line command (sudo apt install sshpass)

# Level 0
```shell
sshpass -p bandit0 ssh bandit0@bandit.labs.overthewire.org -p 2220
```

# Level 1
**flag:** NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
```shell
sshpass -p NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL ssh bandit1@bandit.labs.overthewire.org -p 2220
```

# Level 2
**flag:** rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```shell
sshpass -p rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi ssh bandit2@bandit.labs.overthewire.org -p 2220
```

# Level 3
**flag:** aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG

cd 'file with spaces' (using quotes when file name got spaces)
```shell
sshpass -p aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG ssh bandit3@bandit.labs.overthewire.org -p 2220
```

# Level 4
**flag:** 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe

ls -a (ls --all) shows all entries including those who start with . (los que empiezan con punto son hidden files)
```shell
sshpass -p 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe ssh bandit4@bandit.labs.overthewire.org -p 2220
```

# Level 5
**flag:** lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR

**option 1:** file inhere/* (desde afuera del directorio para mostrar el tipo de cada archivo). _this is my favorite :p_ 

**option 2:** find . -name -file* | xargs file (busca todos los archivos que empiecen con 'file' y el xargs se encarga de tomar cada uno de ellos y aplicarles el file)

CURIOSITY: it's possible to cat even in the same line **_cat $()_**. In this case, we got -> cat $(find . -name -file07)

```shell
sshpass -p lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR ssh bandit5@bandit.labs.overthewire.org -p 2220
```

# Level 6
**flag:** P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU

cat $(find . -size 1033c ! -executable -name '* file*') | cuando ponemos con el signo de admiración negamos que esa -executable y en 1033c el c means bytes
```shell
sshpass -p P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU ssh bandit6@bandit.labs.overthewire.org -p 2220
```

# Level 7
**flag:** z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S

**redirigir salidas, en este caso errores (STDERR) al /dev/null (entiéndase el dev/null como un agujero negro):** 2>/dev/null

_stdin (0), stdout (1), stderr (2)_

cat $(find / -user bandit7 -group bandit6 -size 33c 2>/dev/null)
```shell
sshpass -p z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S ssh bandit7@bandit.labs.overthewire.org -p 2220
```

# Level 8
**flag:** TESKZC0XvTetK0S9xNwm25STk5iWrBvP
it's more efficient to 'grep' a file than 'cat' and then 'grep'. We can also use 'awk' (awk '/millionth/' data.txt)

_grep 'millionth' data.txt_ **more efficient than** _cat data.txt | grep 'millionth'_
```shell
sshpass -p TESKZC0XvTetK0S9xNwm25STk5iWrBvP ssh bandit8@bandit.labs.overthewire.org -p 2220
```

# Level 9
**flag:** EN632PlfYiZbn3PhVK3XOGSlNInNE00t
'uniq -u' shows the unrepeated lines BUT THE LINES MUST BE ORDERED so in this case we'll use 'sort' and then 'uniq' like this -> sort data.txt | uniq -u
```shell
sshpass -p EN632PlfYiZbn3PhVK3XOGSlNInNE00t ssh bandit9@bandit.labs.overthewire.org -p 2220
```

# Level 10
**flag:** G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
let's make a counter to enumerate the lines starting with === with the aim of getting the password -> contador=1; strings data.txt | grep '===' | while read line; do echo "Linea $contador: $line"; let contador+=1; done | awk 'NR==4' | awk 'NF{print $NF}'

'strings' can be used to print the printable character sequences that are at least 4 characters long

'awk NR 4' prints the fourth line

'awk NF print NF' prints the last word of the line por asi decirlo

```shell
sshpass -p G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s ssh bandit10@bandit.labs.overthewire.org -p 2220
```

# Level 11
**flag:** 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
_base64 -d data.txt_ -> convierte un file encripted on base64 with -d to decodificate it
```shell
sshpass -p 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM ssh bandit11@bandit.labs.overthewire.org -p 2220
```




# Level 
**flag:** 
```shell
sshpass -p _ ssh bandit@bandit.labs.overthewire.org -p 2220
```

base64 -d data.txt


