---
layout: post
title: "Bài 8: Member Hiding"
categories: [Junior Developer, Intermediate Scripting]
tags: [Unity, C#]
---
<img src="/assets/images/judev/Unity-2D-and-3D-Games-From-Scratch-and-learn-C-Scripting.jpg" class="fit-image"> 

###### *Loạt bài này dựa trên  <a href="https://learn.unity.com">Khoá Junior Developer</a> của Unity Learn*


### VIII. Member Hiding - Thành viên ẩn


> Loạt bài này nhiều cái lạ quá =)) <br>
> Cái này tui cũng chưa áp dụng bao giờ

Ok, theo những gì tui hiểu á nha. =))

Thì chúng ta có ba class kế thừa chồng nhau vầy nè: (lười tới mức hết dùng gits mà copy code luôn)

Humanoid Class 

```c#
public class Humanoid
{
    //Cái gốc rễ (base) của hàm Yell() nằm ở đây
    public void Yell()
    {
        Debug.Log ("Humanoid version of the Yell() method");
    }
}
```

Enemy Class 

```c#
public class Enemy : Humanoid
{
    // Cái Yell() này ẩn cái Yell() của Humanoid rồi
    // Nghĩa là khi nghi ngta gọi Yell() của instance được khởi tạo từ Enemy thì đảm bảo trả về 
    // "Enemy version of the Yell() method"
    new public void Yell()
    {
        Debug.Log ("Enemy version of the Yell() method");
    }
}
```

Orc Class

```c#
public class Orc : Enemy
{
    // Cái Yell() này ẩn cái Yell() của Enemy rồi
    // Nghĩa là khi nghi ngta gọi Yell() của instance được khởi tạo từ Orc thì đảm bảo trả về 
    // "Orc version of the Yell() method"    
    new public void Yell()
    {
        Debug.Log ("Orc version of the Yell() method");
    }
}
```
     
Giờ thử nhé:


```c#
class GameManager:MonoBehavior{

    void Start(){
        Humanoid human = new Humanoid();
        Humanoid enemy = new Enemy();
        Humanoid orc = new Orc();

        human.Yell();
        enemy.Yell();
        orc.Yell();
    }
}
```

Vậy chung quy lại member hiding là gì, là các class kế thừa có phương thức "new", khi được khởi tạo và gọi phương thức đó thì sẽ ẩn đi phương thức của tổ tiên.

Che đi chứ không có mất nha, giờ ép kiểu ngược về trước thì vẫn xài được phương thức của tổ tiên nhé.

![alt](https://visualstudiomagazine.com/-/media/ECG/visualstudiomagazine/Images/introimages/0116vsm_PVogelTips_IntelliSense.jpg)

Nói thiệt chứ ko hiểu sao Unity lại tách bài 7 và 8 ra luôn ý =))

Tui làm theo giáo trình hoi =)) Mấy ông tự bơi nha.