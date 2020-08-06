# ![](images/Arch_Wall.svg) Arch Wall

- Расположение меню: **Arch → Wall**
- Верстаки: **Arch**
- Быстрые клавиши: **W A**
- Смотрите также: [Arch Structure](Arch_Structure)

## Описание

Этот инструмент создает объект "Стена" с нуля или поверх любого другого объекта на основе формы [shape](Part_Module) или сетки [mesh](Mesh_Module). Стена может быть построена без базового объекта, в этом случае она ведет себя как объем, заданный через длину, ширину и высоту. При построении поверх существующей фигуры стена может базироваться на:

- Линейном 2D объекте **linear 2D object**, таком как линии, ломаные линии, дуги или эскизы, в этом случае вы можете изменить толщину, выравнивание (справа, слева или по центру) и высоту. Длина не имеет значения.
- Плоской грани **flat face**, в этом случае можно изменить только высоту. Длина и ширина не имеют значения. Однако если базовая грань является вертикальной, стена будет использовать ширину вместо высоты, позволяя строить стены из пространственных объектов или формообразующих элементов.
- Твердом теле **solid**,, в этом случае длина, ширина и высота не оказывают никакого влияния. Стена просто использует лежащее в основе тело в качестве своей формы.
- Сетке **mesh**, в этом случае лежащая в основе сетка должна быть замкнутым многогранным телом.

![](images/Arch_Wall_example.jpg)

*Пример стен, построенных из прямой линии, ломаной линии, грани, тела и эскиза*

Стены также могут иметь добавления или вычитания. Добавления - это другие объекты, формы которых объединяются с формой этой стены, а вычитания вычитаются. Добавления и вычитания можно добавлять с помощью инструментов [Arch Add](Arch_Add) и [Arch Remove](Arch_Remove). Добавления и вычитания не влияют на такие параметры стены, как высота и ширина, которые все еще могут быть изменены. Высота стен также может быть выставлена автоматически, если они включены в объект более высокого уровня, например этажи [floors](Arch_Floor "wikilink"). Высота должна быть равна 0, тогда стена примет высоту, указанную в родительском объекте.

Когда несколько стен должны пересекаться, вам нужно поместить их на пол [floor](Arch_Floor "wikilink"), чтобы их геометрия пересеклась.

## Как использовать

### Рисование стены с нуля

1. Выберете **Arch Wall** или нажмите клавишу **W** затем **A**
2. Щелкните первую точку на виде 3D или введите координату [coordinate](Draft_Coordinates "wikilink")
3. Щелкните вторую точку на виде 3D или введите координату [coordinate](Draft_Coordinates "wikilink")

### Построение стены поверх выбранного объекта

1. Выберите один или несколько объектов базовой геометрии (черновик, эскиз и т. д.)
2. Выберете **Arch Wall** или нажмите клавишу **W** затем **A**
3. Настройте необходимые свойства, такие как высота или ширина.

## Параметры

- Стены имеют общие свойства и поведение всех архитектурных компонентов [Arch Components](Arch_Component "wikilink")
- Высоту, ширину и выравнивание стены можно задать во время рисования через панели задач
- При привязке стены к существующей стене, обе стены соединяются в одну. Способ соединения двух стен зависит от их свойств: если они имеют одинаковую ширину, высоту и выравнивание, и если в настройках верстака "Arch" включена опция "Присоединить базовые эскизы (join base sketches)", то результирующая стена будет представлять собой один объект на основе эскиза, состоящего из нескольких сегментов. В противном случае последняя стена будет добавлена к первой в качестве дополнения.
- Нажмите , после первой точки, чтобы ограничить вторую точку на данной оси.
- Чтобы ввести координаты вручную, просто введите цифры, а затем нажмите между каждым компонентом X, Y и Z.
- Нажмите или кликните на флажок, чтобы установить/снять отметку с кнопки Относительно **Relative**. If relative mode is on, the coordinates of the second point are relative to the first one. If not, they are absolute, taken from the (0,0,0) origin point.
- Press while drawing to [constrain](Draft_Constrain "wikilink") your second point horizontally or vertically in relation to the first one.
- Press or the **Cancel** button to abort the current command.
- Double-clicking on the wall in the tree view after it is created allows you to enter edit mode and access and modify its additions and subtractions
- Multi-layer walls can be easily created by building several walls from the same baseline. By setting their Align property to either left or right, and specifying an Offset value, you can effectively construct several wall layers. Placing a window in such a wall layer will propagate the opening to the other wall layers based on the same baseline.
- Walls can also make use of [Multi-Materials](Arch_MultiMaterial "wikilink"). When using a multi-material, the wall will become multi-layer, using the thicknesses specified by the multi-material. Any layer with a thickness of zero will have its thickness defined automatically by the remaining space defined by the Wall's Width value, after subtracting the other layers.

## Привязка

Snapping works a bit differently with Arch walls than other Arch and Draft objects. If a wall has a baseline object, snapping will anchor to the base object, instead of the wall geometry, allowing to easily align walls by their baseline. If, however, you specifically want to snap to the wall geometry, pressing **CTRL** will switch snapping to the wall object.

![](images/Arch_wall_snap.jpg)

## Свойства

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

## Скрипты

The Wall tool can by used in [macros](macros "wikilink") and from the python console by using the following function:

    makeWall ( [obj],[length],[width],[height],[align],[face],[name] ) 
    

- Creates a wall based on the given object, which can be a sketch, a draft object, a face or a solid. align can be "Center","Left" or "Right". If you provide no base object, then you can use numeric values for length, width and height. Face can be used to give the index of a face from the underlying object, to build this wall on, instead of using the whole object.
- Returns the created wall, or None if the operation failed.

Примеры:

    import FreeCAD, Draft, Arch
    baseline = Draft.makeLine(FreeCAD.Vector(0,0,0),FreeCAD.Vector(2,0,0))
    Arch.makeWall(baseline,None,0.1,2)