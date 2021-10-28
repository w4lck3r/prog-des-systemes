## Exercice 17
on a cree deux fichier le premier `test` qui contient 19 characters de 0 donc qui est de taille 20octets. Et le deuxieme un fichier `vide` donc 0 octets.
on cree une archive `test.tar` en lancant la commande `tar -H ustar -c vide test > test.tar`
On utilise la commande `od` pour lire le contenu de l'archive et le decoder a la main, par exemple on execute la commande: `od -Ad -t x1z -v test.tar`
on voit sur le terminal:
```
...
..
.
0010064 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  >................<
0010080 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  >................<
0010096 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  >................<
0010112 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  >................<
0010128 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  >................<
0010144 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  >................<
0010160 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  >................<
0010176 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  >................<
0010192 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  >................<
0010208 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  >................<
0010224 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  >................<
0010240
```
aux positions 636 (512 + 124) à 647 on a:
```
0000624 33 31 36 00 30 30 30 32 34 32 34 00 30 30 30 30  >316.0002424.0000<
0000640 30 30 30 30 30 32 34 00 31 34 31 33 31 35 35 36  >0000024.14131556<
```
la taille du fichier `test.tar` est:
```
00 30 30 30 30  >316.0002424.0000<
0000640 30 30 30 30 30 32 34
```
(donc 00000000024) 

Pour visualiser le contenue du fichier .tar sans l'avoir cree on utilise la commande: `tar -H ustar -c vide test | od -Ad -t x1z -v | less` et éviter ainsi de créer un fichier temporaire test.tar juste pour les tests.

## Exercice 18 (Arrondi au multiple de 512)
* on a cree la fonction arrondi512 de maniere mathematique, le seul cas unique est lorsque `n%512 == 0` le resultat sera le meme nombre passe en parametre `n`. Donc sans arrondissment. 
* Pour remplir un tampon systeme en utilise la commande `read`, pass au deuxieme parametre de la commande une adresse de la structure donne dans l'enonce `posix_header`.
* Pour verifier que le tampon a ete bien rempli on verifie que la valeur retourne par la commande read correspond bien a la taille du structure dans la memoire (et pas -1)
* on compile le programme avec la commande: `gcc arrondi512.c` et on l'execute sur le fichier test.tar avec la commande: `./a.out test.tar` on obtien un valeur en octal donc on doit la convertir en hexadecimal.

* 

## Exercice 19
