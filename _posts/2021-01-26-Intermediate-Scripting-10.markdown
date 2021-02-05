---
layout: post
title: "Bài 10: Interfaces"
categories: [Junior Developer, Intermediate Scripting]
tags: [Unity, C#]
---
<img src="/assets/images/judev/Unity-2D-and-3D-Games-From-Scratch-and-learn-C-Scripting.jpg" class="fit-image"> 

###### *Loạt bài này dựa trên  <a href="https://learn.unity.com">Khoá Junior Developer</a> của Unity Learn*


### X. Interfaces - interface (ko dịch đâu)

> Cái này thấy vậy chứ thuộc hàng cực kì quan trọng luôn <br>
> Nó cách mà ta tạo ra các quy luật ràng buộc, buộc cho các dev khác hay bản thân ta tuân thủ về việc triển khai hành vi cho đối tượng trong Trò chơi

Đầu tiên ta phải tư duy như sau, tách các hành vi của đối tượng ra thành các interface.

<img src ="https://cdn.lynda.com/video/435141-69-635784444436854801_338x600_thumb.jpg" class="fit-image">

Ví dụ về liên minh huyền thoại đi, ta có mấy Type tướng ta? 5 hay 6 gì đó, đại loại là Pháp Sư, Đấu Sĩ, Đỡ đòn, Support, Xạ thủ, Sát thủ. Hết rồi phải ko?

Ok, giờ ta tạo ra các tướng với skill tương ứng. Bằng cách Kế Thừa và Đa hình ư? Quằn chết luôn.

Giờ vầy nhé. Không quan tâm là Type gì, nhưng nhìn chung chúng đều có các đặc tính sau:

```
- CastDirectSpell (chơi skill định hướng)
- CastTargetSpell (chơi skill chọn mục tiêu)
- CastSelfSpell (chơi các skill tại chỗ)
- NormalAtk (đánh thường)
- SelfBuff (tự buff)
- Buff (buff cho người khác lẫn bản thân)
- BuffOther (chỉ Buff cho người khác)
...
```

OK giờ ta triển chúng thành các Interface, nhưng nhiều quá, tui ví dụ với 2 cái là CastDirectSpell vaf Buff thôi nhé.

Cách đặt tên cho interface là thêm chứ I vào tên để tránh nhầm lẫn với class (đọc cho tường minh)

Mấy cái luật viết interface lên google đọc thêm nhé.

```c#
public interface ICastDirectSpellable
{
    void CastSpell();
}
public interface IBuffable
{
    void Buff();
}
```

Giờ thử xài thử nha

```c#
public class Hero1 : MonoBehaviour, ICastDirectSpellable{
    public void CastSpell(){

    }
}
```

```c#
public class Hero2 : MonoBehaviour, IBuffable{
    public void Buff(){
        
    }
}
```
```c#
public class Hero3 : MonoBehaviour, IBuffable,ICastDirectSpellable{
    public void CastSpell(){
        
    }
    public void Buff(){
        
    }
}
```

=)) Tóm lại là như vậy đó, interface xài riêng thì cũng bình thường.

Interface xài chung với đa hình, kế thừa,... thì mới xịn xò con bò.

Ngoài ra, interface còn là một trong những thủ thuật Tag cho GameObject trong Unity (mình sẽ làm bài này sau)

