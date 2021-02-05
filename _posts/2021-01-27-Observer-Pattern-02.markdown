---
layout: post
title: "[2] Observer - Handling Events"
categories: [Junior Developer, Observer]
tags: [Unity, C#, DesignPattern]
pin: true
---
<img src="/assets/images/judev/sky-force-reloaded-unity.png" class="fit-image"> 


______________________

## II. Handling Events - Giải quyết các sự kiện

> Trước tiên mấy ông phải đảm bảo là có được cái game bắn ruồi và đã mở được bằng unity và chạy scene GameScene.unity mà hông hề có lỗi gì cái đã nha.
> Nếu như chưa thì back lại bài 1 tìm link đi nha.
> Nếu như có lỗi thì comment bên dưới tui reply hỗ trợ cho.

Ok, cái game bắn ruồi cung cấp ngữ cảnh để chúng ta triển cái bài này á. Mà mấy ông lưu ý dùm là game bắn ruồi mỗi lần chỉ được bắn 1 viên đạn cho để khi chạm biên trên hoặc chạm quái vật - viên đạn phát nổ thì mới được bắn phát tiếp nha. (Chắc lúc này Kalashnikov chưa làm cây súng liên thanh :v )



Chạy cái scene GameScene.unity và ta phân tích được những gì?
> - Scene được load: Tạo một đối tượng Player Ship ở dưới cùng của screen (và Có một cái shield đính vào Ship)
> - Giữ Mũi tên trái/phải: Di chuyển ship theo phương ngang (Horizontally) , giới hạn là biên bên của screen
> - Nhấn nút space (cách): Ship bắn 1 Projectile (vật được bắn ra) vào không gian theo phương Vector3.up
> - Khi Projectile chạm biên trên của screen: các Projectile bị destroy (remove - xoá).

_____________________________

### Controlling the Rate of Fire -  Phân tích việc Kiểm soát tốc độ bắn

Vấn để tốc độ bắn phụ thuộc vào hai đối tượng < sự kiện >
- PlayerShip < Bắn 1 projectile >
- Projectile < Chạm biên trên màn hình >

<img src="/assets/images/observer/fig2.png" class="fit-image">

Theo như phân tích lúc đầu ta biết được việc bắn 1 projectile là do PlayerShip quyết định. Lúc này, PlayerShip cần return cho những sự kiện này bằng một trong hai cách:

1. Disable Firing (ngừng bắn): Ship sẽ bắn một projectile sau đó ngừng bắn
2. Enable Firing (bắn)

Nhưng đối với Projectile, sự kiện chạm biên trên là do tự nó thực hiện. Nhưng lúc này, sẽ khiến cho PlayerShip được bắn lại (re-enable firing) nên nó cần một sự kiện để bảo với PlayerShip rằng "Ê bắn tiếp đi mày".

<img src="https://i.pinimg.com/564x/64/fc/b0/64fcb0e2bd7b7fdb2e39005363d79bf1.jpg" class="fit-image">

### CÁCH 1: Direct Object Call - Tạm dịch: Chỉ thẳng mặt object mà gọi

Trước khi giải quyết bài toán Kiểm soát tốc độ bắn


>Trở về thời săn bắt hái lượm 1 tí, đây là cách mà hai người ở hai quốc gia giao tiếp với nhau :))<br>
>Muốn nói cái gì với ai cũng phải gặp tận mặt người đó rồi mới nói. Còn hơn tỏ tình. ==!

Đó là concept của cách 1 á.

<img src="https://images-na.ssl-images-amazon.com/images/I/41SmMVsS5iL._AC_SX450_.jpg" class="fit-image">

Giờ mở source game nãy lên, mở cái script `Assets/Scripts/PlayerController.cs` ra đọc đi (script này được đính vào PlayerShip á)<br>

Để ý cái khúc này từ line 67 trở xuống
```c#
public void EnableProjectile() // Xử lý cho phép bắn
{
    ...
}
public void DisableProjectile() // Xử lý ngưng bắn
{
    ...
}
private void FireProjectile() // Xử lý bắn projectile
{
    ...
}
```

Sau đó ngó lên phần Update() sẽ thấy FireProjectile() được gọi mỗi lần nhấn Space.<br>
Ok, giờ thực hiện nhiệm vụ đầu tiên, disable FireProjectile() sau khi bắn.<br>
Bằng cách: đặt một cờ bên trong FireProjectile()

```c#
void Update(){
    if(Input.GetKeyDown(KeyCode.Space)) 
        if (projectileEnabled) {// check cờ projectileEnabled
            FireProjectile(); // thực hiện việc bắn
            DisableProjectile(); // thực hiện cho cờ projectileEnabled = false
        }
}
```
Bước tiếp theo ta cần re-enable việc bắn này lại khi mà projectile chạm biên trên của màn hình.<br>
Nhưng ko may Việc bắn projectile và Việc xử lý ngừng bắn đều nằm bên trong PlayerShip (class PlayerController). <br>

Projectile như ta phân tích ban đầu là nó phải tự biết lúc nào chạm biên trên mà Re-enable việc bắn.

Và như ông thấy, class PlayerController có chưa 1 thuộc tính có kiểu ProjectileController mục đích là để tham chiếu (ref) để Spawn (Instantia) ra rồi set vài thuộc tính của Projectile đó như Speed và Direction. (uầy, set trực tiếp vậy luôn mới chán)

Ok kệ đi, nhờ vậy mà mình biết là Projectile được clone ra sẽ chưa script này. Mình sẽ code thêm vào ProjectileController.<br>
Giờ khi nào mà nó mất thì mình gọi re-enable mà phải ko? Thì KHI NÀO NÓ MẤT? - khi chạm biên trên của màn hình => vậy tìm đoạn code nào chạm biên trên đi!<br>
À đây rồi.


```c#
private void MoveProjectile(){
    transform.Translate(projectileDirection * Time.deltaTime * projectileSpeed, Space.World);
    if (ScreenBounds.OutOfBounds(transform.position)) // khi chạm biên trên của màn hình
        Destroy(gameObject);
}
```

Ok, việc bây giờ là từ đây gọi hàm EnableProjectile(); 

Ở cấp độ tối cổ, muốn gọi được một hàm của class A tại class B thì phải sao? Đảm bảo hai việc này chứ sao:
- Có được Instance (thể hiện) của class A
- Hàm đó của class B phải được public

Sau khi sửa code ta được như sau:

```c#
private void MoveProjectile(){
    transform.Translate(projectileDirection * Time.deltaTime * projectileSpeed, Space.World);
    if (ScreenBounds.OutOfBounds(transform.position)) // khi chạm biên trên của màn hình
    {
        Destroy(gameObject);
        if (isPlayers){
            var playerShip = FindObjectOfType<PlayerController>(); // tìm instance
            playerShip.EnableProjectile(); // nhớ set public cho hàm EnableProjectile
        }    
    }    
}
```

Đảm bảo chương trình hoạt động ko đúng ý ông luôn, tại sao vậy? Vì gameObject chứa chương trình này (ProjectileController) bị destroy trước khi ông thực hiện việc re-enable rồi kìa, đem mấy dòng code kia lên bên trên Destroy(gameObject); đi.

```c#
if (isPlayers){
    var playerShip = FindObjectOfType<PlayerController>();
    playerShip.EnableProjectile();        
}
Destroy(gameObject);    
```

### Tight Coupling - Sự liên kết chặt chẻ

Trước khi đi qua Cách 2, ta phải đánh giá được tại sao cách một bị cho là TỐI CỔ.

Vì nó được liệt vào dạng Tight Coupling, trong lập trình dạng component như Unity. Việc có một Nhiệm vụ của Class A bị class B trỏ trực tiếp vào gọi - được gọi là Tight Coupling - việc này ảnh hưởng lớn đến quan hệ logic của các đối tượng. 

<img src="/assets/images/observer/fig3.png" class="fit-image">

Cái giá phải trả cho việc này:

> 1. Code/Script phình to, mọi chuyện sẽ rối lắm - script phức tạp để mà maintain (bảo trì) hay debug (sửa lỗi). Vậy nên "chạy ngay đi trước khi mọi điều dần tồi tệ hơn"
> 2. Vì phức tạp quá, lệ thuộc nhau quá. Nên khó để viết thêm vào, vì đụng cái này là hư cái kia.
> 3. Khó làm việc nhóm: chỗ nào lệ thuộc bạn phải note lại rồi nhắc cả team code chung rằng "ê chỗ này tao gọi hàm này á nha" :) và thử nghĩ xem bạn phải viết ra bao nhiêu cái note, người ta phải đọc bao nhiêu cái note, chồng chéo nhau mỗi thằng mỗi note. À mà đó là team bạn có viết docs, kiểu team ko viết docs thì hiểu rồi đó :) (như team tui :< )
> 4. Phức tạp để triển khai mấy cái unit test, bạn sẽ ko biết đặt unit test vào chỗ nào luôn á =))

Ngoài ra về hiệu năng, có sẵn instance bằng cách kéo thả ngoài inspector thì không nói. Lỡ mà như trường hợp của game này. Ta phải tìm cho ra instance trong vô số GameObject đang tồn tại trên scene. (lỡ mà một game bự chà bá thì ôi thôi thôi, đừng tưởng tượng nữa ...).
Mà lỡ tìm không ra thì sẽ bị cái ERROR HUYỀN THOẠI  <br>
> Error: Null Reference Exception 

### Cách 2: Delegates and Events - cũng là tiêu đề của post này.

<img src="/assets/images/observer/fig4.png" class="fit-image">

> Ok, để khắc phục các khuyết điểm về Tight Coupling của cách 1, ta sẽ tiến hành cuộc cách mạng đầu tiên của loài Homo Developer là CÁCH MẠNG NHẬN THỨC thông qua việc sử dụng delegates và events

C# trong Unity cung cấp vài tính năng giúp bạn triển khai cái concept event-driven programming (lập trình hướng sự kiện - là cái concept từ đầu tới giờ ta đang theo đuối á - viết code để giải quyết các sự kiện).

Và vấn đề cốt lõi của concept này là DELEGATION

Từ điển định nghĩa: DELEGATION là hành động trao quyền cho một object thay mặt mà làm (hành động).

Trong C#, DELEGATION được triển khai thông qua Delegate Type *(Tui có viết một bài về Delegates [tại đây](https://nhanity.com/2021/01/26/Intermediate-Scripting-15/)) (dô đọc đi chứ phần dưới tui ko giải thích lại về delegate đâu nha - sức chịu đựng có giới thiệu)*

OK triển, code thêm đoạn này vào ProjectileController.cs

```c#
public delegate void OutOfBoundHandler(); // Delegate Type

public class ProjectileController : MonoBehaviour
{
    ...
}
```
Có vài cách để sử dụng Delegates Type này, bài này sẽ dùng Event *( Tui cũng có viết một bài về Event [tại đây](https://nhanity.com/2021/01/27/Intermediate-Scripting-17)) (tính trước rồi - nên bài đó chỉ cách vận hành Event cùng với Delegate luôn á)*

Ok triển, khai báo event với cái kiểu là Delegate vừa tạo bên trong class ProjectileController

```c#
public delegate void OutOfBoundHandler(); // Delegate Type
public class ProjectileController : MonoBehaviour
{
    public event OutOfBoundHandler ProjectileOutOfBounds;

}
```
Rồi cái chỗ xét sự kiện chạm biên trên của màn hình lúc nãy sửa lại thành 

```c#
if (isPlayers){
    // var playerShip = FindObjectOfType<PlayerController>();
    // playerShip.EnableProjectile();
    if (ProjectileOutOfBounds != null)
        ProjectileOutOfBounds();      
}
Destroy(gameObject);    
```

Ok giờ bạn xong ProjectileController rồi á. Những việc bạn vừa làm là init và set-up sự kiện (event). <br>
Giờ bạn phải nạp handler vào event đó thôi! Tất nhiên là class nào chứa method xử lý sự kiện thì class đó sẽ thực hiện việc nạp handler

Ta thêm đoạn sau vào PlayerController.cs
```c#
projectile.ProjectileOutOfBounds += EnableProjectile;
```

Mà biết thêm chỗ nào hông? Để ý nè, nạp Handler (EnableProjectile) vào Event (ProjectileOutOfBounds) của class ProjectileController thì phải tìm cho ra được chỗ nào có instance của class ProjectileController trong PlayerController phải hông? Chỗ nào ta? <br>
Chỗ sinh ra các  projectile clone chứ đâu.

Chèn đoạn code trên vào dòng cuối (hoặc sau đoạn Instantiate) của hàm FireProjectile();

Tới đây tạm xong rồi đó. Nhưng giờ để đảm bảo tính đóng gói và logic của đối tượng PlayerController, ta set private các phương thức EnableProjectile() và DisableProjectile() đi nha. (chuyện cá nhân đừng khoe cho người ngoài biết)

Ok chạy thử đi nha, CHÚC MỪNG BẠN. Lỡ mà có vấn đề gì thì comment bên dưới nhé.

Còn tiếp 2 bài nữa:
- [[Observer] Phần 3: Working with Multiple Subscribers]()
- [[Observer] Phần 4: The Observer Pattern]()