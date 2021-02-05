---
layout: post
title: "Bài 1: Creating Properties"
categories: [Junior Developer, Intermediate Scripting]
tags: [Unity, C#]
---
<img src="/assets/images/judev/Unity-2D-and-3D-Games-From-Scratch-and-learn-C-Scripting.jpg" class="fit-image"> 

###### *Loạt bài này dựa trên  <a href="https://learn.unity.com">Khoá Junior Developer</a> của Unity Learn*


### I. Creating Properties - Tạo thuộc tính

>Tản mạn tí, thật ra lúc đầu học lập trình tui cũng tự hỏi: "thuộc tính (`property`) thì cũng để truy cập rồi đọc ghi giá trị như biến (`variable`) hoi mà?".<br>
>Sau một thời gian dài làm việc với C# cũng như Unity thì tui mới hiểu, đôi lúc mình lười không cần viết `Property` cũng được, nhưng để code tường minh theo OOP cũng như những trường hợp hạn chế quyền "đọc hoặc ghi"hoặc xử lý giá trị mỗi lần "đọc hoặc ghi" mà không cần dựng hàm.<br>
Ta càng tường minh được những vấn đề này, về sau code càng dễ đọc và ít bug.


Thoai lan man quá, đi vào tìm hiểu nào:


Đầu tiên ta tạo một script <b>`Player.cs`</b>,
<br>
Ở script này Player sẽ có 4 thuộc tính chính:
* Chết: IsDie
* Kinh nghiệm: Experience
* Cấp độ: Level
* Máu: Health


Mỗi thuộc tính sẽ tương ứng một `Property`
Như ở ví dụ bên dưới, việc triển khai đầy đủ về thuộc tính Experience là không cần thiết mà có thể viết gọn như Health <br>

><i>Đọc tới đây ta tự hỏi, vậy để public một biến cho rồi? Mắc gì làm `property` chi cho cực?</i><br>


Thật ra `Property` có 2 công dụng chính:
*  Quyết định Phạm vi truy cập cũng như quyền đọc/ghi của một biến/thuộc tính

Cụ thể: Tên là một thuộc tính không thể bị sửa đổi (set) từ class khác nhưng có thể tham chiếu đến giá trị. Việc sống hay chết phụ thuộc vào chính thuộc tính đó chứ không cho đứa khác quyết định.
<script src="https://gist.github.com/tuannhanle/ae441cfeb2522b7e3e08047a8c9cbb3b.js"></script>

*  Thay vì viết một hàm để lấy giá trị một biến đã qua xử lý chỉ số, ta có thể làm một `Properties` tính toán một chỉ số khác để trả về một chỉ số mới. 
Đối với thuộc tính Level, ta có thể thấy công dụng này<br>

Cụ thể, thay vì:
<script src="https://gist.github.com/tuannhanle/08722bea25cd5db7b117ab6ea1570f09.js"></script>

Tổng quan lại:

<script src="https://gist.github.com/tuannhanle/3e53f920c990f4c50410374537a1f1fd.js"></script>

Code gọn và tường minh hơn nhiều phải ko?