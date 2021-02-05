---
layout: post
title: "Bài 4: Generics"
categories: [Junior Developer, Intermediate Scripting]
tags: [Unity, C#]
---
<img src="/assets/images/judev/Unity-2D-and-3D-Games-From-Scratch-and-learn-C-Scripting.jpg" class="fit-image"> 

###### *Loạt bài này dựa trên  <a href="https://learn.unity.com">Khoá Junior Developer</a> của Unity Learn*


### IV. Generics - Không chỉ định kiểu dữ liệu?

> Ok, bài này chủ yếu giải quyết vấn đề của bài trước.<br>
> Hiểu được bài này thì sau này cuộc sống sẽ dễ dàng hơn vì tụi dev dùng cái này CỰC KÌ NHIỀU<br>
> Còn mấy dạng nâng cao của nó thì mấy ông tự tìm hiểu đi nhé, bài này chỉ triển khai cho junior hoi à<br>




<br>

Nhắc lại chuyện cái ao, nhìn code bên dưới các ông thấy 3 hàm (`method`) giống nhau cái gì? <br>

- **Mấy ông**: *giống nhau cái kiểu dữ liệu chứ cái gì?*

Ok mấy ông đúng rồi đó. *(vỗ tay) (làm biến chèn icon)

<script src="https://gist.github.com/tuannhanle/14380dd45cfa12689f36777fc32169a5.js"></script>




Giờ cách giải quyết vầy nè, để cho thằng nào xài cái hàm `Add()` quyết định kiểu dữ liệu trả về, lẫn kiểu dữ liệu truyền vào luôn nhé. 

Mà để cho người ta quyết định thì mấy ông thường dùng biến để lấy cái quyết định của ngta phải ko? Nề, ở đây mình sẽ dùng `Generic`.<br>
Muốn dùng `Generic` thì mấy ông phải `ref` cái này nè nhe.



> using System.Collections;



Rồi viết thành như vầy, tui làm biến tạo thành 2 file gits nên gộp chung nhe.

<script src="https://gist.github.com/tuannhanle/5d5bb569d66c71b3eb153243ef5b6026.js"></script>

Thật ra cái này ứng dụng nhiều vấn đề lắm, mấy ông tra google thêm đi.
Ngoài ra mấy ông còn hiểu đc việc `GetComponent<T>();`

Tui mà là mấy ông, tui học tới đây rồi note cái Generic Method thôi, rồi coi hết series này rồi tra google các ứng dụng khác của Generic.
Thiệt, nhét một lúc nhiều ứng dụng cho 1 bài ko hiệu quả đâu.
