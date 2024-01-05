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

CURIOSITY: it's possible to cat even in the same line 'cat $()'. In this case, we got cat $(find . -name -file07)

```shell
sshpass -p lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR ssh bandit5@bandit.labs.overthewire.org -p 2220
```

# Level 6
**flag:** P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU

cat $(find . -size 1033c ! -executable -name '*file*') | cuando ponemos con el signo de admiración negamos que esa -executable y en 1033c el c means bytes
```shell
sshpass -p P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU ssh bandit6@bandit.labs.overthewire.org -p 2220
```



# Level 
**flag:** 
```shell
```




