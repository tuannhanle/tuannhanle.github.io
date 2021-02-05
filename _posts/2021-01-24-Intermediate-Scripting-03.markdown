---
layout: post
title: "Bài 3: Method Overloading"
categories: [Junior Developer, Intermediate Scripting]
tags: [Unity, C#]
pin: true
---
<img src="/assets/images/judev/Unity-2D-and-3D-Games-From-Scratch-and-learn-C-Scripting.jpg" class="fit-image"> 

###### *Loạt bài này dựa trên  <a href="https://learn.unity.com">Khoá Junior Developer</a> của Unity Learn*


### III. Method Overloading - Viết thêm phương thức (hàm) cùng tên?

>Luyên thuyên, bài này là tiền đề cho bài sau đó nha. Chứ bài này dễ hiểu lắm. Chủ yếu là mấy ông chỉ ra được cái bất cập của cách giải quyết này là ok lắm rồi.<br>
>Sau đó tới bài sau ta giải quyết cái bất cập này.<br>
>Mà nghe có mệt ko chứ, học một giải pháp để giải quyết một bất cập của một giải pháp khác !? :v ?



<br>

Ok, mình sẽ thử viết hàm phép cộng hai số nhé!<br>
Tất nhiên để tránh xung đột kiểu dữ liệu thì mấy ông soạn sẵn mấy cái kiểu trả về và tham số truyền vào theo từng trường hợp của kiểu dữ liệu đó luôn nhé!


<script src="https://gist.github.com/tuannhanle/14380dd45cfa12689f36777fc32169a5.js"></script>

Ok, bài này dễ hiểu cực. Ý là muốn viết nhiều hàm cùng tên (chủ yếu là cùng công năng nhưng hơi khác cách xử lý).<br>
Thì chỉ cần Khác nhau tham số truyền vào (về kiểu hoặc số lượng tham số), hoặc khác nhau về kiểu trả về.

Nghe hao hao giống hàm dựng phải hông?

<img src="https://techvidvan.com/tutorials/wp-content/uploads/sites/2/2020/02/method-overloading-in-java.jpg" class="fit-image"> 

Mà mấy ông thấy lu bu chưa? Nếu cách xử lý phức tạp thì không nói (chịu), đằng này khác nhau mỗi kiểu dữ liệu mà phải viết lại cái hàm như vậy?

Thế là mấy ông kĩ sư C# lười biến phát minh ra cái gọi là Generic để giải quyết vấn đề => bài sau nhé.


