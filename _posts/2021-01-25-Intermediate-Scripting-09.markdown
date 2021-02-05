---
layout: post
title: "Bài 9: Overriding"

categories: [Junior Developer, Intermediate Scripting]
tags: [Unity, C#]
pin: true
---
<img src="/assets/images/judev/Unity-2D-and-3D-Games-From-Scratch-and-learn-C-Scripting.jpg" class="fit-image"> 

###### *Loạt bài này dựa trên  <a href="https://learn.unity.com">Khoá Junior Developer</a> của Unity Learn*


### IX. Overriding - Ghi đè

> Ôi, chánh tông đây rồi.<br>
> Hứa mấy ông luôn cái này ngắn gọn dễ hiểu cực.

Nãy giờ  bài 6-7-8 toàn chỉ kiểu dùng hàm của tổ tiên, hoặc viết mới lại hàm của con nhau cháu phải hông?

Giờ tui muốn cùng 1 một hàm của tổ tiên, class con cháu vẫn thực hiện nội dung của hàm đó kèm thêm việc thực hiện một số việc của con cháu thì sao?

![alt](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b6/Method_overriding_in_subclass.svg/1200px-Method_overriding_in_subclass.svg.png)

Quay lại ví dụ Enemy nhé, tui paste cái script bên dưới kẻo quên.

Với trường hợp này, ông bà phải thêm từ khoá "virtual" để bảo với con cháu rằng, đây là tài sản mà ta để lại cho con trong di chúc.

Con BẮT BUỘC phải nhận, còn xài sao thì tuỳ con.

```c#
class Enemy : MonoBehavior{
    virtual void SayHi(){
        Debug.Log("Tui mới đẻ, tui là enemy nè");
    }
}
```

Ok, giờ đứa con buộc phải nhận ko thôi chương trình báo lỗi biên dịch á =)) 

bằng cách viết lại hàm của tổ tiên kèm từ khoá override

```c#
class Zombie : Enemy{
    virtual void SayHi(){

        Debug.Log("Tui tên là zombie");
    }
}
```

Ủa nhưng mà nãy kêu là xài tiếp nội dung của cha ông mà?

Ok, nếu muốn xài thì phải dùng cú pháp base.TênHàm(); ngay dòng đầu của hàm được override

Cụ thể:

```c#
class Zombie : Enemy{
    virtual void SayHi(){
        base.SayHi();
        Debug.Log("Tui tên là zombie");
    }
}
```

Giờ tui kích hoạt con Zombie cute này nhe.

```c#
class GameManager: MonoBehavior{
    void Start(){
        new Zombie().SayHi(); 
        // Tui mới đẻ, tui là enemy nè
        // Tui tên là zombie
    }

}
```

Lưu ý: Mặc kệ bạn kế thừa xong bạn override lại hàm. Bạn hoàn toàn có thể dùng tính đa hình để biến về "nhân cách" của tổ tiên mà dùng nhé.

Và bạn hoàn toàn có thể gọi thẳng tổ tiên ra dùng luôn.

Cụ thể:

```c#
class GameManager: MonoBehavior{
    void Start(){
        Enemy quaiVat1 = new Enemy();
        quaiVat1.SayHi();
        // Tui mới đẻ, tui là enemy nè

        Enemy quaiVat2 = new Zombie();
        quaiVat.SayHi();
        // Tui mới đẻ, tui là enemy nè
    }
}
```