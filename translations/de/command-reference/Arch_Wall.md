# ![](images/Arch_Wall.svg) Arch Wand

- Menüposition: **Arch → Wand**
- Arbeitsbereich: **Arch**
- Standard Tastenkombination: **W A**
- Siehe auch: [Arch Struktur](Arch_Structure)

## Beschreibung

Dieses Werkzeug erzeugt ein Wandobjekt von Grund auf oder auf Basis eines [Form](Part_Module)- oder [Netzobjektes](Mesh_Module). Eine Wand kann ohne Basisobjekte erstellt werden. In dem Fall verhält es sich als Volumenkörper und verwendet Längen-, Breiten- und Höheneigenschaften. Wenn die Wand auf Basis einer existierenden Form erstellt wird, die Wand kann basieren auf:

- **Linearen 2D-Objekten** wie Linien, Drahtmodellen, Bögen oder Skizzen, wobei Dicke, Ausrichtung (rechts, links oder zentriert) und Höhe angepasst werden können. Die Länge-Eigenschaft hat keinen Effekt.
- Einer **Ebene**, wobei nur die Höhe angepasst werden kann. Die Länge- und Höhe-Eigenschaften haben keinen Effekt. Wenn die Basis-Fläche ist vertikal, die Wand verwendet die Breite-Eigenschaft statt der Höhe. Das ermöglicht das Erzeugen von Wänden von Raum-ähnlichen Objekten oder von Maß-Studien.
- A **solid**, in which case length, width and height properties have no effect. The wall simply uses the underlying solid as its shape.
- A **mesh**, in which case the underlying mesh must be a closed, manifold solid.

![](images/Arch_Wall_example.jpg)

*Example of walls built from a line, a wire, a face, a solid and a sketch*

Walls can also have additions or subtractions. Additions are other objects whose shapes are joined in this Wall's shape, while subtractions are subtracted. Additions and subtractions can be added with the [Arch Add](Arch_Add) and [Arch Remove](Arch_Remove) tools. Additions and subtractions have no influence over wall parameters such as height and width, which can still be changed. Walls can also have their height automatic, if they are included into a higher-level object such as [floors](Arch_Floor "wikilink"). The height must be kept at 0, then the wall will adopt the height specified in the parent object.

When several walls should intersect, you need to place them into a [floor](Arch_Floor "wikilink") to have their geometry intersected.

## How to use

### Drawing a wall from scratch

1. Press the **Arch Wall** button, or press **W** then **A** keys
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

Wand-Objekte erben die Eigenschaften von [Part](Part_Module "wikilink")-Objekten und haben außerdem die folgenden zusätzlichen Eigenschaften:

- **Align**: Die Ausrichtung der Wand an ihrer Basislinie: (links, rechts oder mittig)
- **Base**: Das Basisobjekt, auf dem diese Wand gebaut wurde
- **Face**: Der Index der Fläche des zu benutzenden Basisobjekts. Falls der Wert nicht gesetzt wurde oder 0 ist, wird das gesamt Objekt benutzt
- **Force Wire**: Falls Wahr, und die Wand auf einer Fläche basiert, wird nur die Grenzlinie (border wire) der Fläche benutzt, so dass die Wand die Fläche begrenzt
- **Length**: Die Länge der Wand (wird nicht benutzt, wenn die Wand auf einem Objekt basiert)
- **Width**: Die Breite der Wand (wird nicht benutzt, wenn die Wand auf einer Fläche basiert)
- **Height**: Die Höhe der Wand (wird nicht benutzt, wenn die Wand auf einem Volumen basiert) Wenn keine Höhe gegeben ist und die Wand innerhalb eines [Stockwerk](Arch_Floor "wikilink")-Objekt liegt, verwendet die Wand automatisch die Stockwerkshöhe, falls diese gegeben ist.
- **Normal**: Eine Extrusionsrichtung für die Wand. Wenn auf (0,0,0) gesetzt, ist die Extrusionsrichtung automatisch
- **Offset**: Dies legt den Abstand zwischen der Wand und ihrer Basislinie fest. Das funktioniert nur, wenn die Align-Eigenschaft auf Right (rechts) oder Left (links) gesetzt ist.

## Scripting

Das Wand-Werkzeug kann in [Makros](macros "wikilink") und aus der Python-Konsole heraus durch folgende Funktion angesprochen werden:

    makeWall ( [obj],[length],[width],[height],[align],[face],[name] ) 
    

- Erzeugt eine Wand basierend auf ein gegebenes Objekt, welches eine Skizze, ein Entwurfsobjekt, eine Fläche oder ein Volumen sein kann. Die Ausrichtung kann "Mitte", "Links" oder "Rechts" sein. Wenn kein Basisobjekt angegeben wird, dann können numerische Werte für Länge, Breite und Höhe verwendet werden. Fläche kann dazu genutzt werden, um den Index einer Fläche des zugrundeliegenden Objekts anzugeben, auf dem diese Wand erstellt wird, anstatt das komplette Objekt zu verwenden.
- Gibt die erzeugte Wand zurück, oder None falls die Operation fehlschlägt.

Beispiel:

    import FreeCAD, Draft, Arch
    baseline = Draft.makeLine(FreeCAD.Vector(0,0,0),FreeCAD.Vector(2,0,0))
    Arch.makeWall(baseline,None,0.1,2)