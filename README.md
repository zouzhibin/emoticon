# emoticon 思路
1. 页面首先有一个textarea 输入框 点击发布按钮  还有一个表情图列表
2. 表情图列表其实是每一张图片在代替表情包 在这里我用了六张图片代替六个表情包
3. 点击单独的每个表情包 会把对应得表情包转有属性 添加到输入框 例如[跪了]
4. 然后点击发布的时候 进行正则匹配每个表情包属性 替换成对应得图片路径即可
5. 在这里碰到了一个问题，如何保留文本输入框的换行符空白符，
6. 我想过用正则匹配换行符空白符，然后进行替换，后来发现有一个css的属性特别好用 white-space:pre

## 开启一个表情包组件
- white-space:normal 默认，空白会被浏览器忽略
    normal表示合并空格，多个相邻空格合并成一个空格，在源码中的换行作为空格处理，只会根据容器的大小进行自动换行。
    这里的空白是值空白字符，包括空格，制表符等空白字符，下面为了行文方便，统一用“空格”代表。

### white-space:nowrap不换行
    >  white-space:nowrap和normal一样，也合并空格，但是不会根据容器大小换行，表示不换行。
    white-space:nowrap会导致文本不换行，经常和overflow,text-overflow一起使用

### white-space:pre保留空格不换行
    > white-space:pre的作用是保持源码中的空格，有几个空格算几个空格显示，同时换行只认源码中的换行和<br/>标签。

### white-space:pre-wrap保留空格换行
    > white-space:pre-wrap的作用是保留空格，并且除了碰到源码中的换行和<br/>会换行外，还会自适应容器的边界进行换行。
    white-space:pre-wrap和white-space:pre的区别就是会自适应容器的边界进行换行。

### white-space:pre-line合并空格换行
    > white-space:pre-line的作用是合并空格，换行和white-space:pre-wrap一样，遇到源码中的换行和<br/>会换行，碰到容器的边界也会换
    行。

white-space属性|源码空格|源码换行|<br>换行|容器边界换行
--|:--:|:--:|:--:|:--:|--:
normal|合并|忽略|换行|换行
