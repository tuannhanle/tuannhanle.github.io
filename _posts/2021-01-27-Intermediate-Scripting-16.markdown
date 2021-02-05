---
layout: post
title: "Bài 16: Attributes"
categories: [Junior Developer, Intermediate Scripting]
tags: [Unity, C#]
---
<img src="/assets/images/judev/Unity-2D-and-3D-Games-From-Scratch-and-learn-C-Scripting.jpg" class="fit-image"> 

###### *Loạt bài này dựa trên  <a href="https://learn.unity.com">Khoá Junior Developer</a> của Unity Learn*


### XVI. Attributes - Thuộc tính

> Xài Unity bắt buộc phải biết cái này luôn ý. Nhưng ko cần hiểu bản chất đâu =)) tại tui cũng ko thèm hiểu.

Trước tiên mấy ông muốn hiểu bản chất thì coi [ở đây](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/attributes/).

Đọc hông hiểu phải hông, vậy coi Unity Docs viết gì nè, [ở đây](https://docs.unity3d.com/Manual/Attributes.html)

Ok luôn, cũng hông hiểu phải ko?

Là vậy nè, tui xài cái này theo kiểu học vẹc ý.

Attributes là các thẻ có cú pháp

```
[Tên Attributes] cái gì đó khác theo sau như prop hoặc class
```

Ví dụ

```c#

[HideInInspector]
public float strength; // ẩn field này ở ngoài Unity Editor

[Serializable]
private float weight; // hiển field này ở ngoài Unity Editor

```

Thông qua cái ví dụ cách đặt một thẻ Attributes thì tui cũng nhân tiện nói luôn điều này <br>
Thật ra tui từng hiểu nhầm rằng, `public` là để show cái biến ra ngoài editor (để kéo thả), `private` là để ẩn cái biến đó đi.

> Sai lầm trầm trọng của tuổi trẻ =)) xin lỗi tui từ nghề khác switch qua C#/Unity nên ngáo

Đầu tiên học tới trình junior thì ắt hẳn bạn đã biết là public hay private là phạm vi truy cập chứ liên quan gì cái vụ ẩn hiện kia đâu. <br>
Vậy sao lại vậy? Là do trình Unity Editor nó quy định mặc định vậy thôi, muốn đổi option thì phải đổi value mặc định này phải ko? Mà Unity Editor có phải là một Engine phần mềm hông. <br>
OK, vậy tạm hiểu vầy nhé, muốn get/set cái field của một cái gì đó bên ngoài như Engine, Dll, Plugin,... thì dùng Attributes để quy định.

Thật ra Unity Editor nói riêng hay C# nói chung có rất nhiều thẻ Attributes này tuỳ vào mục đích.<br>
Và ta dùng theo thói quen là chính.

Các thẻ Attributes phổ biến là

```js
[HideInInspector] //Ẩn field ngoài Inspector
[Serializable] // Hiện field ngoài Inspector
[RequireComponent(typeof(Rigidbody)] // Tự động add một Component (ví dụ: Rigidbody) khi class này được nhúng vào Inspector (và component ko xoá được cho đến khi class này được gỡ ra)
[Range(0F,10F)] // Tạo ra một thanh Inspector có biên độ từ 0 đến 10
[Space(1)]  // Cách một khoãng 1 pixel trên Inspector
[DllImport("name.dll")] // Import một Dll vào chương trình (thường là python, c++, swift hoặc java plugin)
...

```

Và còn nhiều nữa, coi thêm [ở đây nè ](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html)

