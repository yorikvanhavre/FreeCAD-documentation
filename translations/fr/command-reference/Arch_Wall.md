# ![](images/Arch_Wall.svg) Mur (atelier Architecture)

- Accès via le menu : **Arch → Mur**
- Atelier : **Arch**
- Raccourci par défaut: **w a**
- Voir aussi : [Élément structurel (atelier Architecture)](Arch_Structure)

## Description

Cet outil génère un objet mur à partir de zéro ou de tout autre objet ayant pour base une [forme](Part_Module) ou [maillage](Mesh_Module). Un mur peut-être généré sans objet de base; dans ce cas il se comporte comme un volume cubique, ayant pour propriétés : longueur, largeur et hauteur. Quand il est généré au-dessus d'un objet existant, un mur peut-être basé sur :

- Un **objet linéaire 2D** (à 2 dimensions) tel qu'une ligne, un fil, un arc ou une esquisse; auquel cas vous pouvez fixer l'épaisseur, l'alignement (droite, gauche ou centré) et la hauteur. La propriété "longueur" est sans effet.
- Une ** face plane**, au quel cas seule la hauteur est modifiable. Les propriétés "longueur" et "largeur" sont sans effet. Cependant, si la face de base est verticale, la propriété valide est la largeur au lieu de la hauteur. Cela permet la génération de mur à partir d'objet "espace" ou d'étude de masse.
- Un **solide**, au quel cas aucune dimension n'est réglable. Le mur se base sur le solide sous-jacent comme il se baserait sur une forme.
- Un **maillage**, au quel cas le maillage en question doit être fermé, ou un quelconque solide.

![](images/Arch_Wall_example.jpg)

*Exemple de murs générés à partir d'une ligne, d'un fil, d'une face, d'un solide et d'un croquis*

Un mur peut subir des additions ou des soustractions. Les additions sont des objets dont les formes sont jointes à la forme du mur; les soustractions suivent le même principe. Les additions et les soustractions peuvent être effectuées avec les outils [Arch Addition](Arch_Add) et [Arch Soustraction](Arch_Remove). Les additions et les soustractions n'ont pas d'influence sur les paramètres du mur tels que la hauteur et l'épaisseur, lesquels peuvent toujours être changés. Un mur peut également avoir une hauteur automatique, si il est inclus dans un objet de niveau supérieur tel qu'un [étage](Arch_Floor "wikilink"). Si la hauteur du mur est fixée à 0, alors le mur héritera de la hauteur spécifiée pour l'objet parent.

Quand plusieurs murs doivent se joindre, il faut les inclure dans un [étage](Arch_Floor "wikilink") pour que leurs géométries fusionnent.

## Comment faire

### Généré un mur à partir de zéro

1. Cliquez sur l'icône **Mur**, ou tapez successivement les touches **w** puis **a**
2. Cliquez sur un premier point de la vue 3D ou saisissez une [coordonnée](Draft_Coordinates "wikilink")
3. Cliquez sur un deuxième point de la vue 3D ou saisissez une [coordonnée](Draft_Coordinates "wikilink")

### Dessiner un mur au-dessus d'un objet sélectionné

1. Sélectionnez un ou plusieurs objets de géométrie de base (objet brouillon, esquisse, etc.)
2. Appuyez sur la touche ** Arch Wall **, ou appuyez sur les touches ** W ** puis ** A **
3. Ajustez les propriétés nécessaires telles que la hauteur ou la largeur.

## Options

- Les murs partagent les propriétés et comportements communs aux [ composants d'Arch ](Arch_Component "wikilink")
- La hauteur, la largeur et l'alignement d'un mur peuvent être définis lors du dessin, via le panneau des tâches
- Lorsque vous accrochez un mur à un mur existant, les deux murs seront joints en un seul. La façon dont les deux murs sont joints dépend de leurs propriétés: s'ils ont la même largeur, la même hauteur et le même alignement, et si l'option "joindre les esquisses de base" est activée dans les préférences d'Arch, le mur résultant sera un objet basé sur une esquisse composé de plusieurs segments. Sinon, ce dernier mur sera ajouté au premier comme ajout.
- Appuyez sur ou après le premier point pour contraindre le deuxième point sur l'axe donné.
- Pour entrer les coordonnées manuellement, entrez simplement les chiffres, puis appuyez sur entre chaque composante X, Y et Z.
- Appuyez ou cliquez sur la case à cocher pour cocher / décocher le bouton ** Relatif **. Si le mode relatif est activé, les coordonnées du deuxième point sont relatives au premier. Sinon, ils sont absolus, tirés du point d'origine (0,0,0).
- Appuyez tout en dessinant sur [ contrainte ](Draft_Constrain "wikilink") votre deuxième point horizontalement ou verticalement par rapport au premier.
- Appuyez sur ou sur le bouton ** Annuler ** pour annuler la commande en cours.
- Un double-clic sur le mur dans l'arborescence après sa création vous permet de passer en mode édition et d'accéder et de modifier ses ajouts et soustractions
- Les murs multicouches peuvent être facilement créés en construisant plusieurs murs à partir de la même ligne de base. En définissant leur propriété Alignée à gauche ou à droite et en spécifiant une valeur de décalage, vous pouvez efficacement construire plusieurs couches de murs. Placer une fenêtre dans une telle couche de mur propage l'ouverture aux autres couches de mur en fonction de la même ligne de base.
- Les murs peuvent également utiliser [ Multi-matériaux ](Arch_MultiMaterial "wikilink"). Lors de l'utilisation d'un multi-matériau, le mur deviendra multi-couche, en utilisant les épaisseurs spécifiées par le multi-matériau. Tout calque d'épaisseur nulle aura son épaisseur définie automatiquement par l'espace restant défini par la valeur de largeur du mur, après soustraction des autres calques.

## Accrochage

L'accrochage fonctionne un peu différemment avec les murs d'Arch que les autres objets d'Arch et Draft. Si un mur a un objet de ligne de base, l'accrochage sera ancré à l'objet de base, au lieu de la géométrie du mur, permettant d'aligner facilement les murs par leur ligne de base. Si, toutefois, vous souhaitez spécifiquement vous accrocher à la géométrie du mur, appuyez sur ** CTRL ** pour basculer l'accrochage sur l'objet mur.

![](images/Arch_wall_snap.jpg)

## Propriétés

Les objets de mur héritent des propriétés des objets [ Part ](Part_Module "wikilink") et ont également les propriétés suivantes et supplémentaires:

- ** Aligner **: l'alignement du mur sur sa ligne de base: gauche, droite ou centre
- ** Bas **: l'objet de base sur lequel ce mur est construit
- ** Face **: L'index de la face de l'objet de base à utiliser. Si la valeur n'est pas définie ou 0, l'objet entier est utilisé
- ** Forcer le fil **: si la valeur est Vraie et que le mur est basé sur une face, seul le fil de bordure de la face est utilisé, ce qui donne un mur bordant la face
- ** Longueur **: La longueur du mur (non utilisé lorsque le mur est basé sur un objet)
- ** Largeur **: La largeur du mur (non utilisée lorsque le mur est basé sur une face)
- ** Hauteur **: La hauteur du mur (non utilisée lorsque le mur est basé sur un solide). Si aucune hauteur n'est indiquée et que le mur se trouve à l'intérieur d'un objet [ étage ](Arch_Floor "wikilink") avec sa hauteur définie, le mur prendra automatiquement la valeur de la hauteur du sol.
- ** Normal **: Une direction d'extrusion pour le mur. Si elle est définie sur (0,0,0), la direction d'extrusion est automatique.
- ** Décalage **: Ceci spécifie la distance entre le mur et sa ligne de base. Fonctionne uniquement si la propriété Align est définie sur Droite ou Gauche.

## Scripting

L'outil Mur peut être utilisé dans les [macros](macros "wikilink") et à partir de la console python en utilisant la fonction suivante:

    makeWall ( [obj],[length],[width],[height],[align],[face],[name] ) 
    

- Crée un mur basé sur l'objet donné, qui peut être une esquisse, un objet dépouillé, une face ou un solide. align peut être "Center", "Left" ou "Right". Si vous ne fournissez aucun objet de base, vous pouvez utiliser des valeurs numériques pour la longueur, la largeur et la hauteur. La face peut être utilisée pour donner l'index d'une face à partir de l'objet sous-jacent, pour construire ce mur, au lieu d'utiliser l'objet entier.
- Renvoie le mur créé ou Aucun si l'opération a échoué.

Example:

    import FreeCAD, Draft, Arch
    baseline = Draft.makeLine(FreeCAD.Vector(0,0,0),FreeCAD.Vector(2,0,0))
    Arch.makeWall(baseline,None,0.1,2)