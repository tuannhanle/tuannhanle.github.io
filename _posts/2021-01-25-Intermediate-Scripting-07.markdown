---
layout: post
title: "Bài 7: Polymorphism"
categories: [Junior Developer, Intermediate Scripting]
tags: [Unity, C#]
pin: true
---
<img src="/assets/images/judev/Unity-2D-and-3D-Games-From-Scratch-and-learn-C-Scripting.jpg" class="fit-image"> 

###### *Loạt bài này dựa trên  <a href="https://learn.unity.com">Khoá Junior Developer</a> của Unity Learn*


### VII. Polymorphism - Đa hình


>   Mấy ông nào biết cái này thì cũng biết cái vụ virtual - override rồi phải hông. <br>
>   Nếu biết rồi thì đây sẽ là một cách viết mới trong Unity.<br>
>   Nếu chưa thì tra google nhé rồi quay lại bài này. <br>

=)) Bản thân tui cũng chưa áp dụng cái kiểu này bao giờ, lúc coi tới đây tui cũng hết hồn.

Ok quay lại ví dụ Enemy ở bài trước.

Giờ tui muốn các class Kế thừa của Enemy, ở mỗi class sẽ có cách xử lý hàm riêng của nó thì sao? 

Bằng cách viết lại hàm đó rồi thêm từ khoá `new` trước kiểu trả về của hàm , ví dụ

```c#
class HeoRung : Enemy {

    public new void SayHi(){
        Debug.Log("Tui tên heo");
    }

}
```

Ok giờ thì thử nhé

```c#
class GameManager:MonoBehavior{

    void Start(){
        var conHeoRung = new HeoRung();
        conHeoRung.SayHi(); // Tui tên heo

        // Nhưng vì nó có tính đa hình, nên giờ biến hình thử nhé
        var quaiVat = (Enemy)conHeoRung;
        quaiVat.SayHi(); // Tui mới đẻ, tui là enemy nè

    }
}
```

Ồ, thì ra khi có tính đa hình rồi, chúng ta có thể biến đổi về "nhân cách" của tổ tiên. Để mà sử dụng các phương thức của tổ tiên

<img src ="https://www.ict.social/images/1/csp/oop/polymorphism.png" class="fit-image">

Cách biến đổi là dùng explicit nhé (ép kiểu tường minh) về tổ tiên của nó cụ thể trong ví dụ trên thì tổ tiên của `HeoRung` là `Enemy`.

Lưu ý, tổ tiên cũng có thể biến đổi "kiểu" về thành con cháu được nhé.

```c#
    HeoRung conHeoNe = (HeoRung) quaiVat; // error liền á.
```

