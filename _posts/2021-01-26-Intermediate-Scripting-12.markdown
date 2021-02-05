---
layout: post
title: "Bài 12: Namespaces"
categories: [Junior Developer, Intermediate Scripting]
tags: [Unity, C#]
pin: true
---
<img src="/assets/images/judev/Unity-2D-and-3D-Games-From-Scratch-and-learn-C-Scripting.jpg" class="fit-image"> 

###### *Loạt bài này dựa trên  <a href="https://learn.unity.com">Khoá Junior Developer</a> của Unity Learn*


### XII. Namespaces - Không gian tên (tên dịch chuối quá)

> Mấy ông có bao giờ thắc mắc mấy cái như using UnityEngine; chưa?
>Ví dụ một ngày đẹp chời bạn tạo các thuộc tính button, text của UI mà unity báo lỗi, ắt hẳn là do bạn thiếu namespace UnityEngine.UI rồi á.

namespace là cách mà C# gom nhóm một số lượng các class có mục tiêu, công dụng, ... như nhau.

Còn việc using namepsace thì để xài các class của nhóm đó chứ gì nữa :))

Khi mà 2 namespace A và B có cùng 1 class có tên là ClassXYZ thì buộc lòng mấy ông phải tường minh ra là A.ClassXYZ hay B.ClassXYZ


