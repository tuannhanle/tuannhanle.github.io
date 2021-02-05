---
layout: post
title: "Bài 13: Lists and Dictionaries"
categories: [Junior Developer, Intermediate Scripting]
tags: [Unity, C#]
pin: true
---
<img src="/assets/images/judev/Unity-2D-and-3D-Games-From-Scratch-and-learn-C-Scripting.jpg" class="fit-image"> 

###### *Loạt bài này dựa trên  <a href="https://learn.unity.com">Khoá Junior Developer</a> của Unity Learn*


### XIII. Lists and Dictionaries - hông dịch được luôn

> Chắc hẳn ai cũng biết dùng Array rồi phải hông <br>
> Chắc hẳn ai cũng biết dựng struct hoặc class rồi phải hông <br>

Array (mảng) có vài vấn đề, đầu tiên khi khởi tạo array phải xác định được độ dài của Array.
Tiếp theo lúc duyệt mảng phải chỉ định được độ dài của mảng. Không thể tăng thêm phần tử trong quá trình sử dụng.

Ok, hai cái yếu điểm đó có thể thay thế bằng List<>, mà List thì có thể linh động convert và Array hoặc Array convert về List được.
Tiện quá.

Vậy nếu giờ tui duyệt một danh sách các item đang có trong shop.
Đầu tiên item là một đối tượng nên nó sẽ có một class đơn giản như sau

```c#
public class Item
{
    public string name;
    public int price;

    //hàm dựng - constructor
    public Item(string newName, int newPrice)
    {
        name = newName;
        price = newPrice;
    }
}
```
Giờ tui muốn tìm một món đồ tên là "Bình MP" để tăng giá chẳng hạn 

```c#
//Code cho vui hoi đừng có bắt bẻ quá :)) mất vui
public class Shop : MonoBehaviour
{
    void Start () 
    {
        List<Item> items = new List<Item>();
        items.Add( new Item("Bình MP", 10));
        items.Add( new Item("Kiếm", 100));
        items.Add( new Item("Giáp", 75));
        items.Sort(); // sắp xếp

        foreach(Item item in items)
        {
            print (item.name + " " + item.price); // in ra cho vui
            if(item.name == "Bình MP"){
                item.price += 5;
            }
        }
        // vừa dài vừa tốn hiệu năng, lỡ mảng có 1000 phần tử rồi phần tử cần truy vấn ở vị trí 1000 rồi sao?
    }
}
```
ok, C# ra đời một thứ gọi là Dictionary - nó giống như một từ điển vậy á, bình thường mình đọc từ điển thì sẽ thấy vầy nè:

> apple : "quả táo"

<img src="https://i.pinimg.com/originals/f8/bf/28/f8bf284607702d9303f288cf5dd60238.jpg" class="fit-image">

Thì Dictionary trong C# cũng tương tự. (tra google để hiểu thêm nhé)
với cú pháp
> Dictionary\<key,value>

```c#
//Code cho vui hoi đừng có bắt bẻ quá :)) mất vui
public class Shop : MonoBehaviour
{
    void Start () 
    {
        // Đỡ phải dựng struct nhỉ, nhưng giả sử value mà phức tạp quá thì cũng phải dựng struct,class nha mấy bạn
        Dictionary<string, int> items = new Dictionary<string, int>();
        items.Add( "Bình MP", 10);
        items.Add( "Kiếm", 100);
        items.Add( "Giáp", 75);
     
        //Giờ muốn thao tác thằng nào, trỏ trực tiếp key của nó luôn, khỏi duyệt List, so sánh gì cả
        items["Bình MP"].price += 5;

    }
}
```




