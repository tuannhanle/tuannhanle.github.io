---
layout: post
title: "Bài 5: Statics"
categories: [Junior Developer, Intermediate Scripting]
tags: [Unity, C#]
---
<img src="/assets/images/judev/Unity-2D-and-3D-Games-From-Scratch-and-learn-C-Scripting.jpg" class="fit-image"> 

###### *Loạt bài này dựa trên  <a href="https://learn.unity.com">Khoá Junior Developer</a> của Unity Learn*


### V. Statics - Từ khoá Statics - tĩnh?

> Bài này có hai cách tiếp cận, một là hiểu công dụng mà ko hiểu bản chất => ok nhưng có bug thì chịu nhé <br>
> Hiểu luôn bản chất => quằn dữ lắm.

Ok, hôm nay ta sẽ học về `static`cho biến (`variable`), hàm (`method`) và lớp (`class`)

<br>

Công dụng của các biến `static` là nó có thể được truy cập từ bất kì đâu thông qua tên lớp (`class`) mà không cần khởi tạo `instance`, và giá trị của các biến này cũng không thay đổi cho đến khi kết thúc chương trình.

Lưu ý: Đối với Unity, một biến `static int a = 1` sẽ luôn bằng 1 kể cả khi `GameObject` chứa `Component/Class` tương ứng bị destroy hoặc chấp luôn các ông đổi scene thì `a vẫn mãi bằng 1` nhé, haha.

<img src="https://i.stack.imgur.com/2cB3s.png" class="fit-image">

Ok giờ tới hàm (method) nhé. Giả sự mấy ông tạo `class TinhToan` , có function `Add(int a, int b)`.

Mỗi lần muốn dùng hông lẽ phải `new Tinhtoan().Add` nhỉ? Cực quá. Thế là mình đặt cho `class` này từ khoá `static` như sau

```c#
    static class Tinhtoan{

        static int Add(int a, int b){

            return a + b;

        }
    }
```


Lưu ý, giả sử bên trong hàm `Add()` vừa rồi có xài một biến cục bộ, thì biến đó cũng phải là `static` nhé. Ví dụ.


```c#
    static class Tinhtoan{
        static int c = 1;
        static int Add(int a, int b){
            
            return a + b + c;

        }
    }
```



Ok, giờ dùng thử nhé.


```c#
    class Khac:MonoBehavior{

        void Start(){
            
            Tinhtoan.Add(1,2); // 4
        }
    }
```

