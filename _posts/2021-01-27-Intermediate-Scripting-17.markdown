---
layout: post
title: "Bài 17: Events"
categories: [Junior Developer, Intermediate Scripting]
tags: [Unity, C#]
pin: true
---
<img src="/assets/images/judev/Unity-2D-and-3D-Games-From-Scratch-and-learn-C-Scripting.jpg" class="fit-image"> 

###### *Loạt bài này dựa trên  <a href="https://learn.unity.com">Khoá Junior Developer</a> của Unity Learn*


### XVII. Events - Sự kiện

> Hổng hiểu nổi, sao Unity Learn ko để bài này ngay sau [bài 15 : Delegate](https://nhanity.com/2021/01/26/15-Intermediate-Scripting-15/) trời?

Ok, lấy lại cái ví dụ bài 15 nha. Nhưng tui viết theo kiểu khác, thêm chữ static và event dô thôi à.

```c#
class GameManager : MonoBehavior{
    public delegate void MyDelegate(int num); 
    public static event MyDelegate MyDelegate;

    [Serializable] private Button button;
    
    void Start(){

        MyDelegate+=Something; // Để ý dấu += có nghĩa là attach
        button.onClick.Addlistener(()=>MyDelegate(123)); // Khi tap button thì trigger MyDelegate()
    })
    

}
```

```c#
class OtherClass : MonoBehavior{

    void OnEnable()
    {
        GameManager.MyDelegate += Something; //attach - đính TUrnCOlor
    }


    void OnDisable()
    {
        GameManager.MyDelegate -= Something;//un-attach
    }

    
    public void Something(int a){
        Debug.Log(a);
    }
}
```

Ví dụ ta có một công việc là In_Ra_Console_Một_Dãy_Số, từ công việc này ta phân tách thành hai khái niệm: Event, Handlle:

```
- Event: Khi nào? Như thế nào?
- Handle: Ra sao?

```

<img src="https://www.tutorialsteacher.com/Content/images/csharp/event-model.png" class="fit-image">

Ở class GameManager, ta ko cần quan tâm sự kiện MyDelegate() sẽ xử lý (handle) cái gì hết. Chỉ cần quan tâm khi nào nó được kích hoạt (trigger) và kích hoạt nó như thế nào (cái gì kích hoạt nó, kích hoạt bao nhiêu lần, trong bao lâu, ...)

Ở phía OtherClass thì ta quyết định vài chuyện. Xử lý công việc đó như thế nào (handle). Tiếp theo ta quyết định xem VIỆC xử lý (handle) này sẽ phụ thuộc vào sự kiện (event) nào. Được nữa thì khi nào lên gỡ phụ thuộc tránh lãng phí tài nguyên và còn để cho một số logic nhất định.

Những gì bản triển khai bên trên được gọi là:

> Publisher/Subscriber Pattern

và còn là tiền đề cho 

> Observer pattern

