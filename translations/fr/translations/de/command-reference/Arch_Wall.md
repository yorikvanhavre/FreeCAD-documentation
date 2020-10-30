# ![](images/Arch_Wall.svg) Arch Wand

- Menüposition: **Arch → Wand**
- Arbeitsbereich: **Arch**
- Standard Tastenkombination: **W A**
- Siehe auch: [Arch Struktur](Arch_Structure)

## Beschreibung

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
2. Click a first point on the 3D view, or type a [coordinate](Draft_Coordinates "wikilink")
3. Click a second point on the 3D view, or type a [coordinate](Draft_Coordinates "wikilink")

### Drawing a wall on top of a selected object

1. Select one or more base geometry objects (Draft object, sketch, etc)
2. Press the **Arch Wall** button, or press the **W** then **A** keys
3. Adjust needed properties such as height or width.

## Optionen

- Walls share the common properties and behaviours of all [Arch Components](Arch_Component "wikilink")
- The height, width and alignment of a wall can be set during drawing, via the task panel
- When snapping a wall to an existing wall, both walls will be joined into one. The way the two walls are joined depends on their properties: If they have the same width, height and alignment, and if the option "join base sketches" is enabled in the Arch preferences, the resulting wall will be one object based on a sketch made of several segments. Otherwise, the latter wall will be added to the first one as addition.
- Press , or after the first point to constrain the second point on the given axis.
- To enter coordinates manually, simply enter the numbers, then press between each X, Y and Z component.
- Press or click the checkbox to check/uncheck the **Relative** button. If relative mode is on, the coordinates of the second point are relative to the first one. If not, they are absolute, taken from the (0,0,0) origin point.
- Press while drawing to [constrain](Draft_Constrain "wikilink") your second point horizontally or vertically in relation to the first one.
- Press or the **Cancel** button to abort the current command.
- Double-clicking on the wall in the tree view after it is created allows you to enter edit mode and access and modify its additions and subtractions
- Multi-layer walls can be easily created by building several walls from the same baseline. By setting their Align property to either left or right, and specifying an Offset value, you can effectively construct several wall layers. Placing a window in such a wall layer will propagate the opening to the other wall layers based on the same baseline.
- Walls can also make use of [Multi-Materials](Arch_MultiMaterial "wikilink"). When using a multi-material, the wall will become multi-layer, using the thicknesses specified by the multi-material. Any layer with a thickness of zero will have its thickness defined automatically by the remaining space defined by the Wall's Width value, after subtracting the other layers.

## Einrasten

Snapping works a bit differently with Arch walls than other Arch and Draft objects. If a wall has a baseline object, snapping will anchor to the base object, instead of the wall geometry, allowing to easily align walls by their baseline. If, however, you specifically want to snap to the wall geometry, pressing **CTRL** will switch snapping to the wall object.

![](images/Arch_wall_snap.jpg)

## Eigenschaften

Wall objects inherit the properties of [Part](Part_Module "wikilink") objects, and also have the following extra properties:

- **Align** : The alignment of the wall on its baseline: Left, right or center
- **Bas** : The base object this wall is built on
- **Face** : The index of the face from the base object to use. If the value is not set or 0, the whole object is used
- **Force Wire** : If True, and the wall is based on a face, only the border wire of the face is used, resulting in a wall bordering the face
- **Length** : The length of the wall (not used when the wall is based on an object)
- **Width** : The width of the wall (not used when the wall is based on a face)
- **Height** : The height of the wall (not used when the wall is based on a solid). If no height is given, and the wall is inside a [floor](Arch_Floor "wikilink") object with its height defined, the wall will automatically take the value of the floor height.
- **Normal** : An extrusion direction for the wall. If set to (0,0,0), the extrusion direction is automatic.
- **Offset** : This specifies the distance between the wall and its baseline. Works only if the Align property is set to Right or Left.

## Scripting

The Wall tool can by used in [macros](macros "wikilink") and from the python console by using the following function:

    makeWall ( [obj],[length],[width],[height],[align],[face],[name] ) 
    

- Creates a wall based on the given object, which can be a sketch, a draft object, a face or a solid. align can be "Center","Left" or "Right". If you provide no base object, then you can use numeric values for length, width and height. Face can be used to give the index of a face from the underlying object, to build this wall on, instead of using the whole object.
- Returns the created wall, or None if the operation failed.

Beispiel:

    import FreeCAD, Draft, Arch
    baseline = Draft.makeLine(FreeCAD.Vector(0,0,0),FreeCAD.Vector(2,0,0))
    Arch.makeWall(baseline,None,0.1,2)