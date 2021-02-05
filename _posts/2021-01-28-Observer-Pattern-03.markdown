---
layout: post
title: "[3] Observer - Working with Multiple Subscribers"
categories: [Junior Developer, Observer]
tags: [Unity, C#, DesignPattern]
---
<img src="/assets/images/judev/sky-force-reloaded-unity.png" class="fit-image"> 


______________________

## III. Working with Multiple Subscribers - Giải quyết với nhiều lượt subscribers

### Introduction and Set up - Giới thiệu và thiết lập.

> Mình nhúng thử cái game WebGL vào đây thử thôi, đừng ai quan tâm nha

<html>
<body>
    <div class="webgl-content">
        <div id="unityContainer" style="width: 100%; height: 100%; padding: 0px; margin: 0px; border: 0px; position: relative; background: rgb(35, 31, 32);"><canvas id="#canvas" style="width: 100%; height: 100%; cursor: default;" width="1200" height="750"></canvas>
            <div class="logo Dark" style="display: none;"></div>
            <div class="progress Dark" style="display: none;">
            <div class="empty" style="width: 0%;"></div>
            <div class="full" style="width: 100%;"></div>
            </div>
        </div>
    </div>
    <script src="/Lego-WebGL/TemplateData/UnityProgress.js"></script>
    <script src="/Lego-WebGL/Build/UnityLoader.js"></script>
    <script>
        var unityInstance = UnityLoader.instantiate("unityContainer", 
        "/Lego-WebGL/Build/WebGL.json", {onProgress: UnityProgress});
    </script>
</body>
</html>

<br><br><br>

Còn tiếp 2 bài nữa:
- [[Observer] Phần 3: Working with Multiple Subscribers]()
- [[Observer] Phần 4: The Observer Pattern]()