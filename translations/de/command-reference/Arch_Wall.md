# ![](images/Arch_Wall.svg) Arch Wand

- Menüposition: **Arch → Wand**
- Arbeitsbereich: **Arch**
- Standard Tastenkombination: **W A**
- Siehe auch: [Arch Struktur](Arch_Structure)

## Beschreibung

Dieses Werkzeug erzeugt ein Wandobjekt von Grund auf oder auf Basis eines [Form](Part_Module)- oder [Netzobjektes](Mesh_Module). Eine Wand kann ohne Basisobjekte erstellt werden. In dem Fall verhält es sich als Volumenkörper und verwendet Längen-, Breiten- und Höheneigenschaften. Wenn die Wand auf Basis einer existierenden Form erstellt wird, die Wand kann basieren auf:

- **Linearen 2D-Objekten** wie Linien, Drahtmodellen, Bögen oder Skizzen, wobei Dicke, Ausrichtung (rechts, links oder zentriert) und Höhe angepasst werden können. Die Länge-Eigenschaft hat keinen Effekt.
- Einer **Ebene**, wobei nur die Höhe angepasst werden kann. Die Länge- und Höhe-Eigenschaften haben keinen Effekt. Wenn die Basis-Fläche ist vertikal, die Wand verwendet die Breite-Eigenschaft statt der Höhe. Das ermöglicht das Erzeugen von Wänden von Raum-ähnlichen Objekten oder von Maß-Studien.
- Einem **Volumen** in dem Fall haben die Länge-, Breite- und Höhe-Eigenschaften keinen Effekt. Die Wand verwendet einfach den darunterligenden Volumenkörper als dessen Form.
- Ein **Netz**, wobei das darunterliegende Netz ein geschlossener Volumenkörper sein muss.

![](images/Arch_Wall_example.jpg)

*Beispiele von Wänden die auf einer Linie, einem Draht, einer Fläche, einem Volumen und einer Skizze aufgebaut werden*

Wände können auch Ergänzungen oder Ausschnitte erhalten. Ergänzungen sind andere Objekte, deren Form mit der Wandform verschmolzen werden. Bei Ausschnitten werden die Formen des anderen Objektes aus der Wand entfernt. Ergänzungen und Ausschnitte können mit dem [Arch Hinzufügen](Arch_Add) bzw. [Arch Entfernen](Arch_Remove) Werkzeug erzeugt werden. Ergänzungen und Ausschnitte haben keinen Einfluss auf Parameter wie Höhe oder Breite, die nach wie vor veränderbar sind. Wände können auch automatisch Höhen erhalten, wenn sie Bestandteil komplexerer Objekte wie [Etagen](Arch_Floor "wikilink") sind. Die Höhe der Wand muss mit 0 festgelegt werden, dann passt sich die Wandhöhe automatisch dem Eltern-Objekt an.

Wenn sich mehrere Wände überschneiden sollen, müssen sie in eine [Etage](Arch_Floor "wikilink") platziert werden, damit sich ihre Geometrien schneiden.

## Verwendung

### Zeichnen einer neuen Wand

1. Drücken Sie den **Arch Wand**-Knopf, oder die Tasten **W** und **A**
2. Klicken Sie einen ersten Punkt in der 3D-Ansicht oder tippen Sie eine [Koordinate](Draft_Coordinates "wikilink")
3. Klicken Sie einen zweiten Punkt in der 3D-Ansicht oder tippen Sie eine weitere [Koordinate](Draft_Coordinates "wikilink")

### Zeichnen einer Wand auf einem selektierten Objekt

1. Selektieren Sie ein oder mehrere elementare Objekte (Draft-Objekt, Skizze, usw.)
2. Drücken Sie den **Arch Wand**-Knopf oder die Tasten **W** und **A**
3. Passen Sie benötigte Parameter wie Höhe und Breite an.

## Optionen

- Wände haben die gleichen Eigenschaften und zeigen das gleiche Verhalten wie alle anderen [Arch-Komponenten](Arch_Component "wikilink").
- Die Höhe, Breite und Ausrichtung einer Wand können während des Zeichnens über das Task-Panel geändert werden.
- Wird eine Wand an einer existierenden Wand ausgerichtet, werden beide Wände zu einer verschmolzen. Die Art der Verschmelzung hängt von den Wandeigenschaften ab: Haben beide die selbe Breite, Höhe und Ausrichtung, besteht die resultierende Wand aus mehreren Segmenten einer Skizze, anderenfalls wird die zweite Wand eine Ergänzung der ersten.
- Drücken Sie die Tasten X, Y oder Z nach dem ersten Wandpunkt, um den zweiten Punkt auf die gegebene Achse zu beschränken.
- Um Koordinaten manuell einzugeben, tippen Sie einfach die Zahlen und drücken anschließend Enter für jede X-, Y- und Z-Komponente.
- Drücken Sie R oder verwenden Sie die **Relativ**-Checkbox, um den Relativmodus zu aktivieren/verlassen. Ist der Relativmodus aktiv, sind die Koordinaten des zweiten Punktes relativ zum ersten Punkt. Anderenfalls sind alle Werte absolut und beziehen sich auf den Koordinatenursprung (0,0,0).
- Press while drawing to [constrain](Draft_Constrain "wikilink") your second point horizontally or vertically in relation to the first one.
- Press or the **Cancel** button to abort the current command.
- Double-clicking on the wall in the tree view after it is created allows you to enter edit mode and access and modify its additions and subtractions
- Multi-layer walls can be easily created by building several walls from the same baseline. By setting their Align property to either left or right, and specifying an Offset value, you can effectively construct several wall layers. Placing a window in such a wall layer will propagate the opening to the other wall layers based on the same baseline.
- Walls can also make use of [Multi-Materials](Arch_MultiMaterial "wikilink"). When using a multi-material, the wall will become multi-layer, using the thicknesses specified by the multi-material. Any layer with a thickness of zero will have its thickness defined automatically by the remaining space defined by the Wall's Width value, after subtracting the other layers.

## Einrasten

Einrasten funktioniert bei Arch-Wänden etwas anders als bei anderen Arch- und Draft-Objekten. Wenn eine Wand ein Basislinien-Objekt hat, erfolgt das Einrasten am Basisobjekt anstatt an der Wand-Geometrie, um Wände einfach an der Basislinie ausrichten zu können. Falls Sie aber speziell an der Wand-Geometrie rasten möchten, wird das Drücken von **Strg** das Einrasten auf das Wand-Objekt ändern.

![](images/Arch_wall_snap.jpg)

## Eigenschaften

Wand-Objekte erben die Eigenschaften von [Part](Part_Module "wikilink")-Objekten und haben außerdem die folgenden zusätzlichen Eigenschaften:

- **Align**: Die Ausrichtung der Wand an ihrer Basislinie: (links, rechts oder mittig)
- **Base**: Das Basisobjekt, auf dem diese Wand gebaut wurde
- **Face**: Der Index der Fläche des zu benutzenden Basisobjekts. Falls der Wert nicht gesetzt wurde oder 0 ist, wird das gesamt Objekt benutzt
- **Force Wire**: Falls Wahr, und die Wand auf einer Fläche basiert, wird nur die Grenzlinie (border wire) der Fläche benutzt, so dass die Wand die Fläche begrenzt
- **Length**: Die Länge der Wand (wird nicht benutzt, wenn die Wand auf einem Objekt basiert)
- **Width**: Die Breite der Wand (wird nicht benutzt, wenn die Wand auf einer Fläche basiert)
- **Height**: Die Höhe der Wand (wird nicht benutzt, wenn die Wand auf einem Volumen basiert) Wenn keine Höhe gegeben ist und die Wand innerhalb eines [Etagen](Arch_Floor "wikilink")-Objekt liegt, verwendet die Wand automatisch die Etagenhöhe, falls diese gegeben ist.
- **Normal**: Eine Extrusionsrichtung für die Wand. Wenn auf (0,0,0) gesetzt, ist die Extrusionsrichtung automatisch
- **Offset**: Dies legt den Abstand zwischen der Wand und ihrer Basislinie fest. Das funktioniert nur, wenn die Align-Eigenschaft auf Right (rechts) oder Left (links) gesetzt ist.

## Skripting

Das Wand-Werkzeug kann in [Makros](macros "wikilink") und aus der Python-Konsole heraus durch folgende Funktion angesprochen werden:

    makeWall ( [obj],[length],[width],[height],[align],[face],[name] ) 
    

- Erzeugt eine Wand basierend auf ein gegebenes Objekt, welches eine Skizze, ein Entwurfsobjekt, eine Fläche oder ein Volumen sein kann. Die Ausrichtung kann "Mitte", "Links" oder "Rechts" sein. Wenn kein Basisobjekt angegeben wird, dann können numerische Werte für Länge, Breite und Höhe verwendet werden. Fläche kann dazu genutzt werden, um den Index einer Fläche des zugrundeliegenden Objekts anzugeben, auf dem diese Wand erstellt wird, anstatt das komplette Objekt zu verwenden.
- Gibt die erzeugte Wand zurück, oder None falls die Operation fehlschlägt.

Beispiel:

    import FreeCAD, Draft, Arch
    baseline = Draft.makeLine(FreeCAD.Vector(0,0,0),FreeCAD.Vector(2,0,0))
    Arch.makeWall(baseline,None,0.1,2)