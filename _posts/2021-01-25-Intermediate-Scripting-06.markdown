---
layout: post
title: "Bài 6: Inheritance"
categories: [Junior Developer, Intermediate Scripting]
tags: [Unity, C#]
pin: true
---
<img src="/assets/images/judev/Unity-2D-and-3D-Games-From-Scratch-and-learn-C-Scripting.jpg" class="fit-image"> 

###### *Loạt bài này dựa trên  <a href="https://learn.unity.com">Khoá Junior Developer</a> của Unity Learn*


### VI. Inheritance - Kế thừa


> Đây là một trong bốn tính chất của lập trình hướng đối tượng, google quá chời bài luôn
> Nhưng áp dụng cho Unity thì như thế nào nhỉ, ý tui là áp dụng cho game ý.

Ok, mấy ông tạo ra 10 con enemy như: Heo rừng, Tê giác, Voi, Ác Ngư, Zombie,...

Mấy ông sẽ kiểu tạo ra 10 class theo tên từng enemy phải hông?

Ok đúng rồi đó, nhưng mà mấy ông có thấy là, có những đặc điểm gì giống nhau ko?

Chúng đều rượt mình, đánh mình, chúng đều có Máu, hay kể cả chúng đều có Mesh Renderer và vân vân mây mây nữa, ...

Có nghĩa là mình phải dựng lại `Rượt()`, `Attack()`, hay các biến như `health`, `meshRenderer`,... hả?

Cực chết luôn!

Ok, ta sẽ áp dụng tính KẾ THỪA vào đây nhé

<image src="https://www.techoschool.com/Images/dotnet_inheritance.jpg" class="fit-image">

Mấy ông dựng một class Enemy chứa mấy cái đó cho tui 

<script src="https://gist.github.com/tuannhanle/8d4678e772d37aa46a741f2edcf22db9.js"></script>

Ok giờ mấy ông chỉ việc kế thừa nó bằng cách class NewClass:Enemy, thử nào

```c#
class ConHeo : Enemy {
    
    void Awake(){
        this.health = 100;
    }

    void Update(){

        this.Ruot();
    }
}
```

Mấy con khác cũng làm như vậy cho tui.

Lưu ý nè:

```html
- từ khoá this là để tường minh cho việc tui 
đang xài hàm hoặc biến được khởi tạo trong phạm
vi của phả hệ chứ không phải hàm hoặc biến cùng
tên ở class nào đó (ngoài phả hệ)

- protected: từ khoá này để chỉ cho việc hàm
hoặc biến có thể được gọi ở chính class đó
hoặc class kế thừa. Trong C# nếu ko khai
báo phạm vi truy cập, mặc định sẽ là protected
```

