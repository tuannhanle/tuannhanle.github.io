---
layout: post
title: "Bài 15: Delegates"
categories: [Junior Developer, Intermediate Scripting]
tags: [Unity, C#]
---
<img src="/assets/images/judev/Unity-2D-and-3D-Games-From-Scratch-and-learn-C-Scripting.jpg" class="fit-image"> 

###### *Loạt bài này dựa trên  <a href="https://learn.unity.com">Khoá Junior Developer</a> của Unity Learn*


### XV. Delegates - Con trỏ hàm

> Delegate là một trong những thứ của C# mà tui vô cùng thích vì nó giúp tui code theo kiểu mà tui hay code với nodejs :v <br>
> tạo ra hàm rồi gán hàm đó vào biến =))

Bạn nào học C/C++ chắc sẽ biết đến khái niệm con trỏ hàm nhỉ.
Còn không thì kệ bạn.

<br><br>

Nhìn dev js người ta dev nè
```js
var something = () => {} // người ta vừa tạo ra một cái hàm đó :)
var somethingElse = () => {}() // người ta vừa tạo ra xong rồi chạy nó luôn đó :)
```

>Thôi Tạm biệt js, khóc xong rồi thì thôi cất gọn poster em vào góc, mình tạm thời không nhìn nhau em nhé.

<br><br>
Delegate gồm có hai phần là Delegate Type (Tương tự một class) và Delegate instance (tương tự một object của class đó)

```c#
    delegate void MyDelegate(int num); //khai báo Delegate Type có 1 tham số int và ko trả về
    MyDelegate myDelegate; // Delegate instance có Type là MyDelegate
```

Ok, bạn vừa tạo ra cái gì vậy. Bạn cũng ko biết?

Giờ giả sử ở đâu đó tồn tại một hàm mà "truyền vào một tham số int và ko có trả về" 

Ví dụ:

```c#
    void Something(int a){

    }
```  

thì bạn hoàn toàn có thể gán hàm đó vào instance "myDelegate" vừa rồi.

```c#
class GameManager : MonoBehavior{
    delegate void MyDelegate(int num); 
    public MyDelegate myDelegate;
    
    void Start(){
        myDelegate=Something; // vi diệu ghê
    }
    
    public void Something(int a){

    }
}
```
Rồi bình thường bạn gọi hàm Something thì sao nhỉ, Something() chứ gì nữa. Giờ sướng lắm, gọi thông qua cái delegate kia kìa. 
```c#
class ClassKhac:MonoBehavior{
    GameManager gameManager;
    void Start(){
        gameManager.myDelegate(1); // trường hợp bạn nạp instance cho gameManager

        // hoặc không thì bạn cho biến myDelegate là static
        GameManager.myDelegate(123);
    }
}
```
<!-- Ủa rồi giờ muốn tháo cái hàm Something(int a) đó ra mà gán cái hàm SomethingElse(int a) thì sao.

Coi bên dưới nè

```c#
// giả dụ GameManager là singleton nha 
// (ý là tui có thể dễ dàng có đc instance của GM 
// thông qua thuộc tính instance của nó)
void Start(){
    GameManager.instance.myDelegate-=GameManager.instance.Something; //un-attach - gỡ ra
    GameManager.instance.myDelegate+=SomethingElse; // attach - gắn vào
}
``` -->

À giờ coi thử xem là C# làm giống tụi js được ko nhé

```c#
Action something = () => {}; // ê được nè
```

Nhưng có hai thứ không bao giờ được:
- Thứ nhất là bạn BẮT BUỘC phải chỉ định (khai báo) delegate type cho một delegate instance, cụ thể ở đây mình dùng Action - là một delagate được dựng sẵn tương đương với một hàm void ko truyền gì vào.
- Thứ hai là bạn KHÔNG THỂ NÀO KÍCH HOẠT nó ngay sau khi tạo vì lúc này something (delegate instance chưa có instance :v ).

<img src="https://miro.medium.com/max/1000/1*JqqQci8d_MHkOeACrr8SOw.jpeg" class="fit-image">

Hiểu tới đây để làm gì
- Học các design pattern áp dụng delegate
- Code delegate nhiều dữ lắm mấy ông ơi!

Bye




