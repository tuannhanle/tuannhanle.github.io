---
layout: post
title: "Bài 11: Extension Methods"
categories: [Junior Developer, Intermediate Scripting]
tags: [Unity, C#]
---
<img src="/assets/images/judev/Unity-2D-and-3D-Games-From-Scratch-and-learn-C-Scripting.jpg" class="fit-image"> 

###### *Loạt bài này dựa trên  <a href="https://learn.unity.com">Khoá Junior Developer</a> của Unity Learn*


### XI. Extension Methods - Phương thức mở rộng

> Đã bao giờ bạn tự hỏi, viết thêm chức năng cho các Class của Unity như GameObject, Transform, ... được hông ta?
> Ê được nha!!

Ok, ta sẽ làm việc đó bằng cách vận dụng Extension Methods - tra google để hiểu thêm 

<img src="https://www.infragistics.com/community/cfs-filesystemfile/__key/CommunityServer.Blogs.Components.WeblogFiles/dhananjay_5F00_kumar.ExtensionMethod/2110.img1.png" class="fit-image">

Ở đây tui chỉ cụ thể trong Unity nè :))

Đầu tiên tui tạo một class có tên bất kì, ở đây tui đặt là NhanityExtension nhé

```c#
public static class NhanityExtension{
    public static void InTenTuiRa(this GameObject go){
        Debug.Log(go.name);
    }
}

```

Giờ xài thử nhé

```c#
public class SomeClass : MonoBehaviour 
{
    void Start () {
        this.gameObject.InTenTuiRa(); // tên gì gì đó
    }
}
```

=)) Ok Mấy ông làm theo vài cái cho mình đi.

```
Lưu ý vài cái thôi:
    - đặt từ khoá static cho hàm và biến của Extentsion nha
    - Với hàm thì nhớ thêm tham số là có kiểu dữ liệu là class mà bạn muốn thêm phương thức (trong ví dụ của tui là GameObject go )
    - Nhớ thêm từ khoá this (hông cần hiểu đâu, kiểu như quy phạm rồi)
    - Chỗ nào xài thì gọi instance của class đó ra rồi gọi Hàm mở rộng - và không cần truyền vào đối số nào cả (mặc kệ tham số đi)

```