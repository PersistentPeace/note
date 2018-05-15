#### 一、颜色
1. 前景色：color
2. 取值
    1. 十六进制：color:#000000~#FFFFFF
    2. RGB格式：如 color:rgb(255,0,0) 即三原色的0~255范围内取值
    3. 颜色名称：如 color:red，注名称前面没有前缀
    4. 实际开发过程中，十六进制用的多一些

#### 二、背景
1. 背景色：background-color，取值同上
2. 背景图：
    1. 背景图地址：background-image:url(图片地址)
        - 图片地址写不写引号都可以
        - url一定要注意，是从当前css文件所在的地址去找图片的地址，不能根据HTML文件的路径去找图片的地址
    2. 背景图重复:background-repeat
        - 当图片大小小于块大小时，图片会重复充满这个区域
        - 横向重复：background-repeat:repeat-x
        - 纵向重复：background-repeat:repeat-y
        - 不重复：background-repeat:no-repeat，就会只显示图片
    3. 背景图位置:background-position
        - 横向：left、 center、 right 或者 0%~100%
        - 纵向：top、 center、 bottom 或者 0%~100%
        - 使用：
            - 横向和纵向各取一个值，如background-position：left top;
            - 百分数的形式：background-position：0% 50%;
    4. 背景图固定：background-attachment
        - 固定：background-attachment：fixed;
3. 背景内容
    ```
    body{
       background-color:red;
       background-image:url(../img/bg.jpg); 
       background-repeat:no-repeat;
       background-position：left top;
       background-attachment：fixed;
    }
    这些代码可以简写为：
    body{
        background：red url(../img/bg.jpg) no-repeat left top fixed;
    }
    基本的顺序为：背景色，背景图，是否重复，位置，是否固定
    ```
#### 三、字体
1. 字体族：font-family
    - 作用：设置多个字体，但使用的时候只能使用一个，目的是当首选字体不能用的时候用第二个，第二个不能用的时候用第三个，以此类推
    - 使用：通常在选择的body标签中使用，如：
    ```
    body{
        font-family：Time, Verdana, "Time New Roman", "微软雅黑";
    }
    注：多个字符的字体要用“”引起来，各字体之间用逗号分开,最后分号结束，表示样式结束
    ```
    - 网上有些好看的字体可能是来字一个链接
2. 字体样式：font-style
    - 正常：font-style：normal;
    - 斜体：font-italic;(印刷斜体)
3. 字号：font-size
    - 直接指定字号 ：如font-size：16px;
    - 相对的方法指定，即在默认的字体大小上扩大/缩小多少倍：如font-size：0.8em;
4. 字体粗细：font-weight
    - 给定值设置：font-weight：400;
    - 加粗：font-weight：bold

#### 四、文本
1. 颜色：同前景色
2. 对齐：text-align
    - 左对齐：text-align：left;
    - 右对齐：text-align：right;
    - 居中：text-align：center;
    - 两端对齐：text-align：justify;(效果不明显)
3. 装饰线：text-decoration
    - 上划线：text-decoration：overline；
    - 贯穿线：text-decoration：line-through；
    - 下划线：text-decoration：underline；
    - <a>标签默认有下滑线，可以自定义取消
4. 转化：text-transform
    - 变大写：text-transform：uppercase;
    - 变小写：text-transform：lowercase；
    - 首字母大写：text-transform：capitalize;
5. 缩进：text-indent
    - 例如：text-indent：100px;表示首行缩进100像素，其他的行不会变化，如果要其他行也缩进也可以，不过要用盒模型的方法。
6. 行间距：line-height
    - 默认行间距是大于字体大小的，否则是两行之间是没有间隙的，所以设置行间距一定要大于字体大小
    - line-height：34px;

#### 五、链接
1. 链接的四种状态
    - 链接状态（什么都不做的状态）：a：link{style1;style2;...}
    - 鼠标经过状态：a:hover{style1;style2...}
    - 正在激活状态：a:active{style1;style2;...}此过程很快，一般看不到
    - 看过之后的的状态：a:visited{style1;style2...}
2. 四种状态的顺序：爱恨（lvha）
    - a:link{}
    - a:visited{}
    - a:hover{}
    - a:active{}
3. 举例：
    ```
    a:link{
        text-decoration:none;
        color:#555;
    }
    a:visited{
        text-decoration:none;
        color:#555;
    }
    a:hover{
        text-decoration:none;
        color:red;
    }
    a:active{
        text-decoration:none;
    }
    链接的在四种状态下都没有下滑线，
    链接状态下字体颜色为灰色
    访问过后的状态为灰色
    鼠标经过的状态为红色
    ```
4. 配合类选择器使用
    - 作用：选择所有链接中的几个单独用一个样式
    - 举例：
    ```
    HTML中：
    <body>
    ...
        <a href="#">点击会变帅<a>
        <a href="#">点击会变帅<a>
        <a href="#">点击会变帅<a>
        <a href="#">点击会变帅<a>
        <a href="#">点击会变帅<a>
        <a href="#">点击会变帅<a>
    </body>
    
    css中：
    a:link{
        text-decoration:none;
        color:#555;
    }
    a:visited{
        text-decoration:none;
        color:#555;
    }
    a:hover{
        text-decoration:none;
        color:red;
    }
    a:active{
        text-decoration:none;
    }
    
    如果此时需要三、四a标签与其他的标签的样式不一样，可以配合类选择器：
    HTML中：先给个class
    <body>
    ...
        <a href="#">点击会变帅<a>
        <a href="#">点击会变帅<a>
        <a class="foot" href="#">点击会变帅<a>
        <a class="foot" href="#">点击会变帅<a>
        <a href="#">点击会变帅<a>
        <a href="#">点击会变帅<a>
    </body>
    css中：同过类选择器选中三四a标签，然后：
    a.foot:link{
        text-decoration:none;
        color:#555;
    }
    a.foot:visited{
        text-decoration:none;
        color:#555;
    }
    a.foot:hover{
        text-decoration:none;
        color:red;
    }
    a.foot:active{
        text-decoration:none;
    }
    这么做的主要是因为a标签有四种状态，否则的话我们直接用类选择就可以定义样式了。
    ```
#### 六、列表
1. 列表标识样式：list-style-type
    - 使用以下样式的前提是先用选择器选中元素
    - 不要列表标识：list-style-type：none;
    - 无序列表常用：
        - 列表标识为方块：list-style-type：square;
        - 列表标识为圆圈：list-style-type：circle;
    - 有序列表常用：
        - 列表标识为罗马字：list-style-type：upper-roman;
    - 有序、无序列表都选中：
    ```
    ul，ol li{style1，style2...} 
    标识有序及无序列表中的li元素样式为...
    ```
2. 位置：list-style-position
    - 外部：list-style-position：inside；
    - 内部：list-style-position：outside；
3. 图片：list-style-image
    -  作用：将列表前面的列表标识变成一个图片
    -  方法：list-style-image：url(xx.jpg)

#### 七、表格
1. 通过css让表格有边框:border
    ```
    补充：快速改某些东西，比如所有的<td></td>里面加上hello，
    可以将<td></td>替换为<td>hello</td> 
    html中：
    <table>
        <tr>
            <td>hello</td>
            <td>hello</td>
            <td>hello</td>
        </tr>
        <tr>
            <td>hello</td>
            <td>hello</td>
            <td>hello</td>
        </tr>
        <tr>
            <td>hello</td>
            <td>hello</td>
            <td>hello</td>
        </tr>
    </table>
    css中：
    table,th,td {
        border:1px solid #000;
    }
    ```
2. 边框线折叠：border-collapse：
    ```
    table{
        border-collapse:collapse;
    }
    这样会显示单线效果
    ```
3. 表格布局：table-layout
    ```
    table{
        width:400px;
        table-layout:fixed;
    }
    表示表格固定400px大小
    ```
4.  隐藏空的单元格：empty-cells
    ```
    table{
        empty-cells：hide;
    }
    ```

#### 补充：
HTML中div可以加设置宽高：
```
HTML中：
<div id="bg"><div>

css中：
#bg{
    width:500px;
    height:500px;
    border:1px
}
```

