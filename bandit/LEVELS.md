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


# Level 12
**flag:** JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
using ROT13 (rotar letra por la #13 siguiente) with _tr_ -> cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'

tr 'lo que se quiere reemplazar' 'a lo que se va a a reemplazar'
**example:** echo 'hola k ase' | tr 'a' 'e'   ->   _hole k ese_
```shell
sshpass -p JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv ssh bandit12@bandit.labs.overthewire.org -p 2220
```

# Level 13
**flag:** wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw

this level sounds like [A Saucerful of Secrets](https://www.youtube.com/watch?v=cEfS98F89Ho). to reverse the hex dump and copy it into another file we use __xxd -r name_of_the_file > new_file__, and let's _file_ (el comando para ver el tipo de archivo) that new file and we'll see it's a gzip, then we apply gzip -d or bzip2 -d depending on the type of the file. IT'S IMPORTANT TO _MV_ (change file names _mv quierocambiareste.txt lepongoestenombre.gz_) THE FILES TO CHANGE THE EXTENSIONS IN ORDER TO BE ABLE TO APPLY GZIP OR BZIP2.
```shell
sshpass -p wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw ssh bandit13@bandit.labs.overthewire.org -p 2220
```

# Level 14
**flag:** fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq

_ssh bandit14@bandit.labs.overthewire.org -p 2220 -i filewithprivatekey_ -> lo usamos para acceder a bandit como lo hemos vendido haciendo con SSH con una private key as a file. ESE FILE QUE CONTENGA LA PRIVATE KEY NO DEBE TENER ACCESO DE GRUPO NI DE USUARIO PARA QUE SEA UN ARCHIVO PROTEGIDO Y ASI PUEDA SER USADO (se cambian los permisos con _ghmod 700 filewithprivatekey_).

PD: no olvidar copiar la private key que está en el ls de bandit13 en un archivo en su computadora (first you must exit from overthewire server). Esto se puede hacer con "echo PASSWORD > private.key"
```shell
sshpass -p fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq ssh bandit14@bandit.labs.overthewire.org -p 2220
```

# Level 15
**flag:** jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

it's important to read about _netcat_ -> sintaxis: nc HOST PORT

nc localhost 30000 // (localhost = 127.0.0.1)
```shell
sshpass -p jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt ssh bandit15@bandit.labs.overthewire.org -p 2220
```

# Level 16
**flag:** JQttfApK4SeyHwDlI9SXGR50qclOAil1

echo "jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt" | openssl s_client -connect localhost:30001 -ign_eof

read about openssl and use it with s_client command to send an encrypted message using echo and then the pipe. -ign_eof ignores the [EOF sign](https://baulderasec.wordpress.com/programando-2/programacion-c-por-la-practica/capitulo-iv/caracter-fin-de-fichero/#:~:text=El%20valor%20EOF%20es%20un,m%C3%A1s%20datos%20disponibles%20para%20leer.) en la entrada estándar
```shell
sshpass -p JQttfApK4SeyHwDlI9SXGR50qclOAil1 ssh bandit16@bandit.labs.overthewire.org -p 2220
```

# Level 17
**flag:** VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e

nmap -p 31000-32000 localhost

then, what I did was the same as level 16 (send a message with echo to each port I found with nmap) and finally found a SSH private key so I did the same thing as level 14.

_ssh bandit17@bandit.labs.overthewire.org -p 2220 -i private.key_

REMEMBER: to see the password in clear text in levels like this, we use -> _cat /etc/bandit_pass/bandit17_

```shell
sshpass -p VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e ssh bandit17@bandit.labs.overthewire.org -p 2220
```

# Level 18
**flag:** hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg

diff passwords.old passwords.new
```shell
42c42
< p6ggwdNHncnmCNxuAt0KtKVq185ZU7AW
---
> hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
```
42c42 indica que la diferencia ocurre en la línea 42. La parte que comienza con < indica la línea en el archivo original passwords.old, y la parte que comienza con > indica la línea en el nuevo archivo passwords.new
```shell
sshpass -p hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg ssh bandit18@bandit.labs.overthewire.org -p 2220
```

# Level 19
**flag:** awhqfNnAbc1naukrpqDYcF95h7HoMTrC

sshpass -p hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme

"If a command is specified, it will be executed on the remote host instead of a login shell". In this case, the command is _cat readme_
```shell
sshpass -p awhqfNnAbc1naukrpqDYcF95h7HoMTrC ssh bandit19@bandit.labs.overthewire.org -p 2220
```

# Level 20
**flag:** VxCazJaVykI6W36BkBU0mJTCM8rR95XT

Al igual que el nivel anterior, ejecutamos el comando directamente para obtener la contraseña. En este caso, al hacer ls -l nos damos cuenta que bandit20-do ya tiene el setuid y es un executable. Entonces -> _./bandit20-do cat /etc/bandit_pass/bandit20_
```shell
sshpass -p VxCazJaVykI6W36BkBU0mJTCM8rR95XT ssh bandit20@bandit.labs.overthewire.org -p 2220
```

# Level 21
**flag:** NvEJF7oVjkddltPSrdKEFOllh9V1IBcq

Use 2 terminals. La primera, execute the executable in any port. La segunda, _nc -l -v -p port_ (ESE port DEBE SER EL MISMO QUE SE USÓ EN LA PRIMER TERMINAL)

```shell
sshpass -p NvEJF7oVjkddltPSrdKEFOllh9V1IBcq ssh bandit21@bandit.labs.overthewire.org -p 2220
```

# Level 22
**flag:** WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff

cd /etc/cron.d

cat cronjob_bandit22

cat /usr/bin/cronjob_bandit22.sh

```shell
sshpass -p WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff ssh bandit22@bandit.labs.overthewire.org -p 2220
```
# Level 
**flag:** 
```shell
sshpass -p _ ssh bandit@bandit.labs.overthewire.org -p 2220
```

