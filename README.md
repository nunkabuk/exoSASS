# SASS pour : Syntactically Awesome Style Sheets  

SASS([site officiel](http://sass-lang.com/guide)) est un langage de feuilles de style en cascade (CSS) qui sera compilé pour obtenir du CSS.  

Permet principalement d'utiliser des variables dans vos CSS, permet aussi facilement l'import de fichiers scss dans d'autres fichiers scss et  donc découper et organiser ces styles en plusieurs fichiers pour travailler à plusieurs sur une application qui au final produiront un seul fichier grâce à la commande sass.

Le résultat peut également être compressé en passant une option à la ligne de commande pour avoir une feuille de style plus rapide à charger pour vos visiteurs, les plus efficace étant compressed , compact
option possible de compression : nested (default), compact, compressed, ou expanded  
 exemple pour compresser vos fichiers scss :  
̀```
sass --watch chemin_fichiers_scss:chemin_fichiers_css --style compressed
̀̀```

- Comparaison du code SASS / SCSS   

La syntaxe originale , nommée « syntaxe indentée », vous pourrez donc croisé des fichiers avec l'extension .sass, qui est l'ancien format. La nouvelle syntaxe se nomme « SCSS » avec l'extension .scss. Elle a un formalisme proche de CSS(avec les accolades).  

La différence : l'indentation pour le SASS et les accolades pour SCSS  
![Sass Vs Scss Vs CSS](sass-vs-scss.png)  

- Installation:
```
sudo apt install ruby
```

- Puis:  
```
sudo gem install sass
```

- Créer un répertoire assets/scss et assets/css  

! Ne créez rien dans assets/css ! c'est la commande sass que vous avez installé plus haut qui va créer les fichiers css automatiquement pour vous à partir du code scss que vous allez mettre dans vos fichiers scss :  

Tutoriels pour en savoir plus:  
[https://la-cascade.io/se-lancer-dans-sass/](https://la-cascade.io/se-lancer-dans-sass/)  
[https://www.alsacreations.com/article/lire/1717-les-preprocesseurs-css-c-est-sensass.html](https://www.alsacreations.com/article/lire/1717-les-preprocesseurs-css-c-est-sensass.html)

Essayez d'appliquer les styles ci-dessous :  

Nous allons créer plusieurs partiels comme dans ce dépôt:  
[Exemple de répertoire SCSS contenant des partiels](https://github.com/MyClientisRich/WPbaseTheme/tree/master/scss)  
- Utilisation de variables :
```
Créer un fichier assets/scss/_colors.scss est mettre dedans :  
```
```
$fond: #222;
$texte: #AAA;

$base_color: #48A3E9;
```
- Créer un fichier assets/scss/app.scss et importez dedans le fichier \_colors.scss ci-dessus en mettant dedans:  
```
@import nomdufichierSansLextensionSCSS
```
Dans app.scss, affectez au body un background en lui affectant la variable $fond comme couleur et comme couleur de police la variable $texte  

- Pour voir le résultat de tout cela, utilisez la commande ci-dessous pour compiler et tester vos fichiers SCSS ci-dessus et linkez le app.css obtenu dans index.html.
Lancez la commande ci-dessous une seule fois dans le terminal, elle observera automatiquement les changements que vous faites dans les fichiers scss et re-créera automatiquement le fichier de style app.css:
```
sass --watch assets/scss/app.scss:assets/css/app.css --trace --style compressed
```

- Nesting ( traduction : Le fait de nicher des données/éléments dans un.e autre.
 )
 exemple :
 ```
 a {
     color: $link_color;
     &:hover {
         color: $color_hover;
     }
     &:focus {
         color: $color_focus;
     }
}
```
```
Créer un fichier assets/scss/_liste.scss
```
Mettez et modifiez le nesting ci-dessous pour affecter à la liste .listDeux uniquement un lien blue et lime au hover :  
```
ul {  
    padding: 0;
    li {
        list-style: none;
        a {
            color: blue;
            &:hover {
                color: lime;
            }
        }
    }
}
```

Pareil pour la liste de box3 ( .listTrois ), couleur du lien en jaune et grise au survol.
```
importez dans app.scss le fichier _liste.scss et observez le style des liens dans index.html
```

- Inheritance ( Héritage )   
```
%box {
    margin: 5px;
    padding: 5px;
    border: 1px solid black;
}

.greenBox {
    @extend %box;
    border-color: lime;
}

.greenBoxBlueBackground {
    @extend .greenBox;
    background-color: blue;
}
```
Créez un héritage %box comme ci-dessous, vous pouvez l'utiliser ensuite avec le mot clef @extend dans vos classes box1, box2 et box3 pour ajouter ces propriétés automatiquement.

-----

Pour voir une utilisation avancée de SASS, regardez le contenu du fichier \_headings.scss à la racine du projet, il y a des variables, boucles afin de générer des styles...  
Déplacez le fichier \_headings.scss dans assets/scss/ et importez le dans app.scss pour voir les modifications qui va ajouter dans app.css et visionnez le resultat dans index.html
