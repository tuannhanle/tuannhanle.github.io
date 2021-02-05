---
layout: post
title: "[1] Observer - Project Overview"
categories: [Junior Developer, Observer]
tags: [Unity, C#, DesignPattern]
pin: true
---
<img src="/assets/images/judev/sky-force-reloaded-unity.png" class="fit-image"> 


______________________

## I. Project Overview - Tổng quan dự án

> Trước khi đi vào nội dung, tui xin giới thiệu loạt bài này dựa trên concept bài giảng của Marc Gilbert ([Linkedin](https://www.linkedin.com/in/marcdgilbert/))

______________________

Vào lúc nào đó trong giai đoạn đầu của nghiệp lập trình game của ông, ông sẽ phải đối mặt với vài câu hỏi đại loại như:
> - Làm sao để tui cập nhật UI khi player tấn công ?
> - Làm sao bảo với tụi enemy là màn game kết thúc rồi (tụi mày biến đi)?

Và còn vô số tình huống mà ở đó - vài thứ đang diễn ra sẽ làm thay đổi một trong vô số các GameObject của ông - và điều đó có nghĩa là code của ông cần có một sự GIAO TIẾP giữa các đối tượng (GameObject)

<img src="/assets/images/observer/fig1.png" class="fit-image">

Như đầu hết mọi điều trong C# và Unity, ông có vài đối tượng - làm vài việc nhất định.

Trong C# có một Design Pattern để implement (thực hiện) việc này đó là OBSERVER PATTERN.

ông sẽ khám phá vài kiểu Observer và thấy rằng rất phê khi áp dụng chúng vào một con game thực sự của ông.

______________________

## Getting Started - Bắt đầu ngay

> Chúng ta sẽ cày cái Design Pattern này thông qua một con game, cụ thể là dạng game bắn ruồi (2D Arcade Shotter). 

Mấy ông [tải ở đây](https://connect-prd-cdn.unity.com/20210125/42169301-2c66-4d76-ba8a-094844d7c1b0/ObserverDemo.zip?_ga=2.251267841.626714653.1611538975-1287089369.1611212879)

______________________

## Target - Mục tiêu

Thông qua ví dụ này mấy ông sẽ hiểu được 4 khái niệm sau trong lập trình C#:
> - Tổng quát về Giao tiếp gián đoạn ( *Interrupted Object Communications*)
> - Sự đa dạng trong cách giao tiếp của từng đối tượng, việc nhiều đối tượng return cho một sự kiện (*Multiples object responding to singple event*)
> - Observer Design Pattern là cái quái gì? :v
> - Và bước tiếp đến Publisher-Subscriber Pattern

Đồng thời ta được học 

> - Cách triển cái Observer này vào dự án game của mình như thế nào.
> - Giống và khác nhau giữa Observer và đa hướng (*C# multicast delegates*).


CHÚC VUI :)

Chúc bản thân tui nữa, viết blog nhọc vl, đó h đọc chùa quen rồi :<

Còn tiếp 3 bài nữa:
- [[Observer] Phần 2: Handling Events](https://nhanity.com/2021/01/27/Observer-Pattern-02/?query=02)
- [[Observer] Phần 3: Working with Multiple Subscribers]()
- [[Observer] Phần 4: The Observer Pattern]()

_________________________