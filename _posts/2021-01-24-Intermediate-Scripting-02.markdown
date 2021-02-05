---
layout: post
title: "Bài 2: Ternary Operator"
categories: [Junior Developer, Intermediate Scripting]
tags: [Unity, C#]
pin: true
---
<img src="/assets/images/judev/Unity-2D-and-3D-Games-From-Scratch-and-learn-C-Scripting.jpg" class="fit-image"> 

###### *Loạt bài này dựa trên  <a href="https://learn.unity.com">Khoá Junior Developer</a> của Unity Learn*


### II. Ternary Operator - Toán tử bậc ba

> Chắc hẳn bạn đã quen với `IF(){}ELSE{}` rồi phải hông, thật ra có cách viết gọn như thế nhiều mà rất nhiều ngôn ngữ sử dụng chứ hổng riêng gì C# cả. Hôm nay mình sẽ chỉ các bạn sử dụng `toán tử bậc ba`.
> Nói thiệt nhe, mục đích biết cái này là để đọc script người khác viết hoi chứ mấy ông viết gì mà hổng đc, hổng chừng viết `IF-ELSE` còn tường minh hơn á.

<br>

Mình sẽ làm theo ví dụ của Unity luôn là "Kiểm tra máu của `Player`, nếu lớn hơn `0` thì return `"sống"`, ngược lại thì return `"nghẻo"`.

Bình thường mình sẽ viết như vầy nè phải hông?

<script src="https://gist.github.com/tuannhanle/4ae2488142bee2f4d3daec4ca5951465.js"></script>

Ok, giờ viết lại cho ngầu chỉ với 1 dòng nè.
1. Đầu tiên mấy ông xác định xem điều kiện là gì?
2. Nếu đúng thì sao?
3. Nếu sai thì sao? 
4. Tiếp theo cần xác định xem cái field nào cần đc ghi?

OK, nếu đã xong thì mấy ông viết lại dưới dạng vầy nè

` 4 = 1 ? 2 : 3;`

Hổng hiểu nữa thì

` field = điều kiện ? giá trị 1 : giá trị 2; `

<img src="https://static.javatpoint.com/cpages/images/conditional-operator-in-c.png" class="fit-image"> 

Ví dụ:

<script src="https://gist.github.com/tuannhanle/b5e0921e191348f888ac28c5c83c97d3.js"></script>

Lưu ý, toán tử này chỉ áp dụng cho mấy cái trường hợp mà kết quả của mệnh đề đúng lẫn sai đều có thể gán vào field.

Ok mấy ông viết thử đi nhé.


