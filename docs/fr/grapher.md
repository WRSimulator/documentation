# Grapheur

Ce module permet de dessiner un chronogramme (jusqu'à 16 variables) pendant la simulation :
![](fr/media/image84.png)

- Il faut préalablement préparer la liste des variables à visualiser dans une zone texte éditée dans WinRelais, par exemple :

(**19 - demo_Variateur_ATV31_triphasé_3C.xrs**)
![](fr/media/grapher2.png)

- Il faut que la première ligne de la zone de texte commence par le mot clef **Grapheur**,
- cette zone texte peut-être placée librement dans le schéma,
- une icone spécifique apparait pendant la simulation si la zone texte **Grapheur** est détectée,
![](fr/media/grapher3.png)

- l'ordre des variables détermine l'ordre d'affichage du chronogramme,
- la syntaxe utilisée pour définir une variable est : **nom_de_l'objet.commande[.calibre]**

| commande|description                |exemple|
| -------------- | ------------ |----------------|
|state|état actif/non actif|fdc_haut.state : état du fin de course haut|
|speed|vitesse objet moteur|M1.speed : vitesse du moteur M1|
|direction|sens de rotation objet moteur|M1.rotation : sens de rotation du moteur M1|
|value.calibre|valeur mesurée et calibre|A1.value.10 : courant mesuré par l'ampèremètre A1 calibré 10 A|







