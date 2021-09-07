# ![](images/Arch_Wall.svg) Mur (atelier Architecture)

- Accès via le menu : **Arch → Mur**
- Atelier : **Arch**
- Raccourci par défaut: **w a**
- Voir aussi : [Élément structurel (atelier Architecture)](Arch_Structure)

## Mô tả

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
2. Nhấp vào một điểm đầu tiên trên khung hình 3D, hoặc gõ vào một [toạ độ](Draft_Coordinates "wikilink")
3. Nhấp vào một điểm thứ hai vào khung hình 3D, hoặc gõ vào một [toạ độ](Draft_Coordinates "wikilink")

### Vẽ một Tường trên một đối tượng chọn trước

1. Chọn một hoặc nhiều đối tượng hình học cơ bản (đối tượng Nháp [Draft], phác thảo, v. v.)
2. Bấm phím **Kiến trúc - Tường**, hoặc bấm phím **W** sau đó là phím **A**
3. Điều chỉnh các tham số cần thiết, chẳng hạn như chiều cao hoặc chiều rộng.

## Các tuỳ biến

- Các Tường chia sẻ các đặc tính tính và hành vi chung của tất cả các [Kiến trúc - Cấu kiện](Arch_Component "wikilink")
- Chiều cao, chiều rộng và canh lề của một Tường có thể được đặt trong khi vẽ, sử dụng Bảng nhiệm vụ
- Khi bắt ngang một Tường vào một Tường khác đã có, thì cả hai Tường sẽ được gắn với nhau thành một đối tượng Tường. Cách mà hai Tường nối với nhau phụ thuộc vào các đặc tính của chúng: Nếu chúng có cùng chiều dày, chiều cao và kiểu canh lề, và nếu tuỳ biến “Ghép các phác thảo cơ bản” được chọn trong các mặc định ưu tiên của Kiến trúc, thì đối tượng Tường nhận được sau khi ghép nối sẽ là đối tượng dựa trên phác thảo của các phân đoạn. Nếu không thì đối tượng Tường được chọn sau sẽ được thêm vào như là phần nối dài của đối tượng Tường được chọn trước.
- Bấm , hoặc sau điểm đầu tiên để ràng buộc điểm thứ hai trên trục đã cho.
- Để nhập các toạ độ kiểu thủ công, chỉ cần nhập giá trị bằng số, rồi bấm dấu cách giữa các thành phần nhập X, Y, và Z.
- Bấm hoặc nhấp chuột vào ô kiểm để chọn hoặc bỏ chọn phím **Tương đối **. Nếu chế độ Tương đối được bật, các tọa độ của điểm thứ hai là tương đối so với điểm thứ nhất. Nếu không, thì các giá trị này là các giá trị tuyệt đối, tính từ điểm gốc tọa độ (0,0,0).
- Bấm trong khi vẽ để [ràng buộc ](Draft_Constrain "wikilink") điểm thứ hai theo phương ngang và theo phương đứng tương đối so với điểm đầu tiên.
- Bấm phím **Hủy bỏ** để hủy bỏ câu lệnh hiện thời.
- Nhấp kép vào Tường trong cây hiển thị sau khi nó được tạo ra sẽ cho phép bạn vào chế độ soạn thảo và truy cập và sửa đổi thêm bớt chúng
- Tường nhiều lớp có thể được tạo ra bằng cách đặt các Tường với cùng một đường cơ sở. Bằng cách đặt thuộc tính canh lề của chúng về trái hoặc về phải, và chỉ ra giá trị định khoảng [giá trị offset], bạn có thể dựng được các lớp của Tường một cách hiệu quả. Việc đặt một cửa sổ trong một lớp tường sẽ dẫn đến việc mở các lớp tường khác mà có cùng một đường cơ sở.
- Các đối tượng Tường cũng có thể sử dụng [Đa Vật liệu ](Arch_MultiMaterial "wikilink"). Khi sử dụng dạng đa vật liệu, Tường sẽ trở thành có nhiều lớp, với các chiều dày được xác định bởi khai báo đa vật liệu. Một lớp bất kỳ có chiều dày bằng không sẽ có chiều dày được xác định một cách tự động bằng khoảng không gian còn lại từ giá trị Chiều dày Tường trừ đi chiều dày các lớp khác.

## Chế độ bắt dính

Chế độ bắt dính của Tường trong gói Kiến trúc có khác đôi chút với chế độ bắt dính của các đối tượng khác trong gói Kiến trúc và gói Bản nháp. If a wall has a baseline object, snapping will anchor to the base object, instead of the wall geometry, allowing to easily align walls by their baseline. Tuy nhiên, nếu bạn đặc biệt muốn bắt dính theo tham số hình học của Tường, thì việc bấm **CTRL** sẽ chuyển chế độ bắt dính vào đối tượng Tường.

![](images/Arch_wall_snap.jpg)

## Các đặc tính [thuộc tính]

Wall objects inherit the properties of [Part](Part_Module "wikilink") objects, and also have the following extra properties:

- **Align** : The alignment of the wall on its baseline: Left, right or center
- **Bas** : The base object this wall is built on
- **Face** : The index of the face from the base object to use. Nếu giá trị là không thiết lập hoặc 0, thì toàn bộ đối tượng được sử dụng
- **Force Wire** : If True, and the wall is based on a face, only the border wire of the face is used, resulting in a wall bordering the face
- **Length** : The length of the wall (not used when the wall is based on an object)
- **Width** : The width of the wall (not used when the wall is based on a face)
- **Height** : The height of the wall (not used when the wall is based on a solid). Nếu chiều cao không được xác định, và Tường ở bên trong một đối tượng [tầng](Arch_Floor "wikilink") với chiều cao đã được xác định của nó, thi Tường sẽ tự động lấy giá trị chiều cao tầng.
- **Normal** : An extrusion direction for the wall. Nếu đặt bằng (0,0,0), hướng trồi ra sẽ được tự động xác định.
- **Offset** : This specifies the distance between the wall and its baseline. Có hiệu lực chỉ khi thuộc tính Canh lề được đặt bằng Phải hoặc Trái.

## Câu lệnh

Công cụ Tường có thể được sử dụng trong [vĩ lệnh](macros "wikilink") từ dấu nhắc lệnh của python như sau:

    makeWall ( [obj],[length],[width],[height],[align],[face],[name]) 
    

- Tạo ra một Tường dựa trên đối tượng obj cho trước, có thể là một Phác thảo, một đối tượng Nháp, một Mặt hoặc một Khối. align có thể là "giữa", "trái" hoặc "phải". Nếu không cho biết đối tượng cơ sở, thì có thể sử dụng các giá trị bằng số cho chiều dài, chiều rộng và chiều cao. Face có thể được sử dụng để đưa ra chỉ số của một mặt từ đối tượng cơ sở, dựa vào đó để xác định Tường, thay vì việc sử dụng toàn bộ đối tượng.
- Câu lệnh sẽ tạo ra Tường hoặc không tạo ra gì cả nếu khi thực thi gặp lỗi.

Ví dụ:

    import FreeCAD, Draft, Arch 
    baseline = Draft.makeLine(FreeCAD.Vector(0,0,0),FreeCAD.Vector(2,0,0)) 
    Arch.makeWall(baseline,None,0.1,2)