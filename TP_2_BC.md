# Exercice 1

1)
bash trouve les commandes tapées par l’utilisateur dans le dossier /home de l’utilisateur.

2)
La variable d’environnement permettant à la commande cd tapée sans argument de nous ramener dans notre répertoire personnel est CDPATH.

3)
Le rôle des variables locales suivantes est :
LANG : Définit la langue régional utilisé
PWD : signifie “print working directory” c’est le répertoire courant
OLDPWD : signifie “OLD Print Working Directory” était le répertoire courant avant la dernière utilisation de la commande cd.
SHELL : correspond à l'emplacement du shell utilisé (exemple : /bin/shell)

4)
on crée la variable local MY_VAR avec :
```
MY_VAR=x
```
et on vérifie que la variable existe avec :
```
echo $MY_VAR
```
ce qui renvoie ‘x’

5)
La commande bash crée une nouvelle session bash la variable MY_VAR n’existe donc plus car il s’agit d’une variable locale propre à 'l'ancienne' session.

6)
On crée la variable d’environnement MY_VAR avec :
```
export MY_VAR
```
Cette variable n'étant plus une variable ‘locale’ mais une variable d'environnement, elle existe donc dans les autres sessions bash.

7)
```
NOM='Baptiste Coquelet'
export $NOM
echo $NOM
```
8)
voici une commande qui aﬀiche ”Bonjour à vous, prénom nom !”.
echo Bonjour à vous, $NOM !

9)
Lorsque l’on utilise la commande unset sur une variable cette variable est détruite alors que si on donne une valeur vide a une variable cette variable ‘existe’ encore.

10)
la commande :
```
echo '$HOME' = $HOME
```
Ecrira la phrase ‘$HOME = chemin (où chemin est votre
dossier personnel d’après bash)’

# Exercice 2

 ```bash
#!/bin/bash

PASSWORD="aze"
read -s -p "saisser votre mot de passe : " input
if [ _$input == _$PASSWORD ]; then
	echo -e "\nBon mot de passe"
	else
	echo -e "\nMot de passe incorrecte"
fi
```
  

# Exercice 3

```bash
#!/bin/bash

function is_number()
{
	re='^[+-]?[0-9]+([.][0-9]+)?$'
	if ! [[ $1 =~ $re ]] ; then
		return 1
		else
		return 0
	fi
}

is_number $1
if [ $? -eq 0 ]; then
	echo -e "\nEst un nombre réel"
	else
	echo -e "\nN'est pas un nombre réel"
fi
```

# Exercice 4
```bash
#!/bin/bash
if compgen -u | grep -q -w $1 ;
	then
	echo "true"
else
	echo "false"
fi
```
# Exercice 5
```bash
#!/bin/bash

VAR=1

for i in $(seq 1 $1)
	do
	VAR=$(($VAR * $i))
done
echo $VAR
```
# Exercice 6
```bash
#!/bin/bash
rand=$((RANDOM%1000+1))

while [1 -eq 1];do
	read x
	if [$x -gt $rand] then
		echo "C’est moins !"
	elif [$x -gt $rand] then
		echo "C’est plus !"
	else
		echo "Gagné !"
		break
	fi
done

```
# Exercice 7
```bash
#!/bin/bash

declare -a array
count=0
while [ $count -eq 3 ]; do
    echo -n "donner 3 entier : "
    read currentNumber
    count=$count+1
        array+=($currentNumber)
done

echo ${array[@]}
min=0
max=0
moyenne=0
i=1
for i in "${array[@]}"; do
    if [ $i -eq 1 ]; then
        min=$i
        max=$i
        moyenne=$((moyenne + $i))
    else
        if [ $i-lt $min ]; then
            min=$i
        elif [ $i-gt $max ]; then
            max=$i
        fi
        moyenne=$((moyenne + $i))
    fi
    i=$((i + 1))
done
moyenne=$((moyenne / $i))
echo min: $min
echo max: $max
echo moyenne: $moyenne
```
