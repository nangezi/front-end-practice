#  CSS选择器总结

##  一、 选择器类型

### 1. 简单选择器
#### 1.1  通用选择器
匹配页面中所有的元素。
   ```
   *{ marigin:0 }
   ```
#### 1.2 元素选择器
```
p { background-color:balck }
```
   
#### 1.3 类选择器
元素使用class属性命名，多个元素可以使用同一class。
```
.nav{background-color:red; color:white; }
```
   
#### 1.4 id选择器
元素使用id属性，id具有唯一性。
```
#level-1{margin:10px;}
```
#### 1.5 分组选择器
对元素选择器进行分组，多种元素同一样式，区别于class选择器。
```
p,h1,h2{color:black}
```
### 2. 组合选择器
#### 2.1 后代选择器
匹配属于指定元素后代的所有元素。包括子子孙孙。
```
div p{background-color:yellow}
```
#### 2.2 子选择器
匹配指定元素的子元素。所有直系儿子，后代不算。
```
div > p {background-color:yellow}

```
#### 2.3 相邻兄弟选择器
匹配指定元素的相邻同级的元素。同一个爹，紧跟着的第一个兄弟。
```
div + p{background-color:yellow}
```
#### 2.4 通用兄弟选择器
匹配指定元素的同级元素。所有兄弟。并且指定元素的后面兄弟。
```
div ~ p{background-color:yellow}
```
### 3. 伪类选择器
定义元素的特殊状态。比如：鼠标悬停，已访问链接和未访问链接，元素获得焦点。
#### 3.1 锚伪类
链接能以不同的方式显示
```
selector：pseudo-class {property: value;}
```
定义顺序 (先后关系)：
link = visied > hover > active

伪类和CSS类结合使用
鼠标悬停链接是改变颜色；
#### 3.2 first-child
伪类与指定元素匹配：第一个子元素
```
first-child{color:blue}
/*p的第一个i儿子*/
p i:first-child {color: blue}
/*第一个p的所有i儿子，伪类加后代的感觉*/
p:first-child i {color: blue}
```
#### 3.3 lang伪类
为不同语言定义特殊规则。
```
/*为属性为lang="en"的<q>元素定义引号*/
q:lang(en){ quotes:"~" "~"}
```
#### 3.4 :focus伪类
```
input:focus{background-color: yellow;}
```
### 4. 伪元素选择器
设置元素指定部分的样式。
例如：首字母、首行的样式，在元素内容之前或之后插入内容。
```
selector::pseudo-element{property: value;}
```
#### 4.1 ::first-line伪元素
文本首行添加特殊样式，且只能用于块级元素。
```
p::first-line{color:red;font-size:xx-large;}
```
#### 4.2 ::first-leter伪元素
文本首字母添加特殊样式。只能应用于块级元素。
```
p::first-leter{color:red;font-size:xx-large;}
```
伪元素与类结合：
```
p.intro::first-leter{color:red;font-size:xx-large;}
```
#### 4.3 ::before

在元素内容之前插入一些内容。
```
h1::before {
  content: url(smiley.gif);
}
```
#### 4.3 ::after

在元素内容之后插入一些内容。
```
h1::after {
  content: url(smiley.gif);
}
```

#### 4.4 多个伪元素可以结合使用
::first-line和::first-letter可以结合使用。

### 5. 属性选择器
选取带有指定属性的元素。
#### 5.1 CSS [attribute] 选择器
```
a[target] {background-color: yellow;}
```
#### 5.2 CSS [attribute="value"] 选择器
选取带有指定属性和值的元素。

#### 5.3 CSS [attribute~="value"] 选择器
选取属性值包含指定词的元素。

#### 5.4 CSS [attribute|="value"] 选择器
选取指定属性以指定值开头的元素。值必须是完整或单独的单词。

#### 5.5 CSS [attribute^="value"] 选择器
选取指定属性以指定值开头的元素。值不必是完整的单词。

#### 5.6 CSS [attribute$="value"] 选择器
选取指定属性以指定值结尾的元素。值不必是完整单词。

#### 5.7 CSS [attribute*="value"] 选择器
选取属性值包含指定词的元素。值不必是完整单词。

## 二、选择器的优先级
### 1. 三大特性
继承：子类继承父类的样式。

优先级：不同类样式的权重比较。

层叠：数量相同时，后者覆盖前者。

### 2. 不同级别
!important > 行内样式 > ID选择器 > 类选择器 > 元素 > 通用 > 继承 > 浏览器默认属性
### 3. 同一级别
后写覆盖先写
### 4. 优先级的计算规则：
1.  每个规则对应一个初始“四位数”：a=0、b=0、c=0、d=0
1. 行内对应：a;
   
   id = b;
   
   class/属性/伪类 = c;

   元素/伪元素 = d
2. 对应数相加得到的“a-b-c-d”，从左到右比较，大的优先级最高

