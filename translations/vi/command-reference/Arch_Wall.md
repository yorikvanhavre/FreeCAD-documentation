# ![](images/Arch_Wall.svg) Kiến trúc - Tường

- Vị trí menu: **Kiến trúc → Tường**
- Gói công cụ: **Kiến trúc**
- Phím tắt mặc định: **W A**
- Xem thêm: [Kết cấu Kiến trúc](Arch_Structure)

## Mô tả

Công cụ này xây dựng một đối tượng Tường từ đầu hoặc trên một đối tượng [dựa trên] [hình dạng](Part_Module) hoặc trên một đối tượng [dựa trên] [lưới chia](Mesh_Module) đã có. Một Tường có thể được xây dựng trực tiếp mà không cần dựa vào đối tượng cơ sở nào. Khi đó, nó là một khối với các thuộc tính dài, rộng và cao. Khi được xây dựng từ một đối tượng đã có, một Tường có thể được dựa trên:

- Một **đối tượng 2D tuyến tính**, ví dụ như các đường, các đường lưới, các đường cong, hoặc các phác thảo, mà trong các trường hợp này, bạn có thể thay đổi chiều dày, canh lề (phải, trái hoặc giữa) và chiều cao. Không cần khai báo đặc trưng chiều dài.
- Một **mặt phẳng**, trong trường hợp này bạn chỉ có thể thay đổi chiều cao. Không thay đổi được [không cần khai báo] các đặc trưng chiều dài và chiều rộng. Tuy nhiên, nếu mặt này theo phương đứng, Tường sẽ sử dụng đặc trưng chiều rộng thay vì chiều cao, cho phép bạn xây dựng các bức tường từ các đối tượng kiểu như 3D hoặc từ các đối tượng dạng khối.
- Một [đối tượng] **khối **, trong trường hợp này thì các đặc trưng chiều dài, chiều rộng và chiều cao đều không cần khai báo. Tường sẽ lấy luôn các đặc tính này của đối tượng khối.
- Một **lưới**, trong trường hợp này lưới phải là một khối kín nhiều mảnh.

![](images/Arch_Wall_example.jpg)

*Ví dụ về các Tường được xây dựng từ một đường, một đường lưới, một mặt, một khối hoặc một phác thảo*

Có thể thực hiện các phép toán cộng và trừ đối với các đối tượng Tường. Trong phép cộng, hình dạng của các đối tượng khác được ghép thêm với hình dạng của Tường, trong khi đó, phép trừ thì trừ đi. Phép cộng và phép trừ có thể được bổ sung bằng các công cụ [Kiến trúc - Cộng](Arch_Add) và [Kiến trúc - Trừ](Arch_Remove). Phép cộng và phép trừ không ảnh hưởng đến các tham số tổng thể của Tường như là chiều cao và chiều rộng, các tham số này vẫn có thể thay đổi. Các Tường cũng có thể có chiều cao được thay đổi tự động, nếu chúng được đặt vào trong một đối tượng cấp cao hơn, chẳng hạn như các [sàn](Arch_Floor "wikilink"). Khi chiều cao được đặt bằng 0, thì Tường sẽ lấy giá trị chiều cao theo chiều cao được xác định trong đối tượng [bố mẹ] cấp cao hơn.

Khi một số Tường giao nhau, bạn cần phải đặt chúng vào một mức [sàn](Arch_Floor "wikilink") để có dạng hình học của chúng được giao cắt nhau.

## Cách dùng

### Vẽ một Tường từ đầu

1. Bấm phím **Kiến trúc - Tường**, hoặc bấm phím **W** sau đó là phím **A**
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
- Double-clicking on the wall in the tree view after it is created allows you to enter edit mode and access and modify its additions and subtractions
- Tường nhiều lớp có thể được tạo ra bằng cách đặt các Tường với cùng một đường cơ sở. Bằng cách đặt thuộc tính canh lề của chúng về trái hoặc về phải, và chỉ ra giá trị định khoảng [giá trị offset], bạn có thể dựng được các lớp của Tường một cách hiệu quả. Việc đặt một cửa sổ trong một lớp tường sẽ dẫn đến việc mở các lớp tường khác mà có cùng một đường cơ sở.
- Các đối tượng Tường cũng có thể sử dụng [Đa Vật liệu ](Arch_MultiMaterial "wikilink"). Khi sử dụng dạng đa vật liệu, Tường sẽ trở thành có nhiều lớp, với các chiều dày được xác định bởi khai báo đa vật liệu. Một lớp bất kỳ có chiều dày bằng không sẽ có chiều dày được xác định một cách tự động bằng khoảng không gian còn lại từ giá trị Chiều dày Tường trừ đi chiều dày các lớp khác.

## Chế độ bắt dính

Chế độ bắt dính của Tường trong gói Kiến trúc có khác đôi chút với chế độ bắt dính của các đối tượng khác trong gói Kiến trúc và gói Bản nháp. Nếu một Tường có một đường cơ sở, việc bắt dính sẽ neo vào đối tượng cơ sở thay vì neo vào các tham số hình học của Tường, cho phép canh lề Tường một cách dễ dàng theo đường cơ sở của chúng. Tuy nhiên, nếu bạn đặc biệt muốn bắt dính theo tham số hình học của Tường, thì việc bấm **CTRL** sẽ chuyển chế độ bắt dính vào đối tượng Tường.

![](images/Arch_wall_snap.jpg)

## Các đặc tính [ thuộc tính]

Các đối tượng Tường thừa hưởng các thuộc tính của đối tượng [Bộ phận](Part_Module "wikilink"), và cũng có các thuộc tính khác sau đây:

- **Canh lề**: Canh lề Tường trên đường cơ sở của nó: trái, phải hoặc ở giữa
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

Ví dụ:

    import FreeCAD, Draft, Arch 
    baseline = Draft.makeLine(FreeCAD.Vector(0,0,0),FreeCAD.Vector(2,0,0)) 
    Arch.makeWall(baseline,None,0.1,2)