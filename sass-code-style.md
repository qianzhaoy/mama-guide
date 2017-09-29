# Sass 和 css 编码规范

## 选择器


### 合理避免使用ID

一般情况下ID不应该被应用于样式。ID的样式不能被复用并且每个页面中你只能使用一次ID。

### 选择器避免使用标签名

当构建选择器时应该使用清晰，准确和有语义的class(类)名。不要使用标签选择器。如果你只关心你的class(类)名，而不是你的代码元素，这样会更容易维护。


###选择器尽可能精确
#### 不直接使用后代选择器 `空格`
解释: 有时，这有可能带来BUG,并且可能会很耗性能, 因为后代选择器会遍历父元素的DOM树的最后一层, 不管你父元素是否有此后代. 除非在HTML设计上用后代选择更好, 更通用.不然尽量使用子选择器 `>`
```css
//bad
.content .title {
  font-size: 2rem;
}

//good
.content > .title {
  font-size: 2rem;
}

```

## 写法

###  尽量缩写属性
```css
//bad
padding-bottom: 2em;
padding-left: 1em;
padding-right: 1em;
padding-top: 0;

//good
padding: 0 1em 2em;

```

### 单位
建议省略 **"0"** 值后面的单位.

```css
//bad
padding-bottom: 0px;
margin: 0em;

//good
padding-bottom: 0;
margin: 0;

```

### 继承
使用继承时，如果在声明块内书写 `:extend` 语句，必须写在**开头**：

```sass
//good
.error {
  border: 1px #f00;
  background-color: #fdd;
}
.seriousError {
  @extend .error;
  border-width: 3px;
}
```

### 私有属性前缀
同一属性有不同私有前缀的，尽量按前缀长度降序书写，**标准形式必须写在最后**。且这一组属性以第一条的位置为准，尽量按冒号的位置对齐。

```css
.box {
    -webkit-transform: rotate(30deg);
       -moz-transform: rotate(30deg);
        -ms-transform: rotate(30deg);
         -o-transform: rotate(30deg);
            transform: rotate(30deg);
}
```


##嵌套和缩进

### 缩进
IDE使用同一缩进格式的插件.

###嵌套

1. 使用嵌套的时候, 避免嵌套过深, 以**三层**为最大嵌套层数.

2. 嵌套中引入 空行
```sass
//good
.content {
  display: block;
 
  > .news-article {
    background-color: #eee;
 
    > .title {
      font-size: 1.2em;
    }
 
    > .article-footnote {
      font-size: 0.8em;
    }
  }
}
```





