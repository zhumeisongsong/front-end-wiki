Sass Styleguide

## 1,嵌套不要超过三层  

嵌套太多层的缺点：
  
- 不利于复用  
- 需要在其他页面修改的时候，需要更大的优先级才能修改成功，只会增加更多的嵌套。

bad 

```
.wrapper {
    .content {
      .title {
        p {
          font-size: 12px;
        }
      }
    }
  }
```
good
```
.title {
    p {
      font-size: 12px;
    }
  }
```

## 2,不要给id赋样式 

缺点：
  
- 不利于复用（毕竟不是每个页面都会有相同的id）  
- 代码不够清晰，一般来说id是为了操作DOM,class才是给DOM元素加样式的。


## 3,基础格式
- 使用 2 个空格作为缩进。
- 类名建议使用破折号代替驼峰法。如果你使用 BEM，也可以使用下划线（[参考链接](https://github.com/airbnb/css)）。
- 在一个规则声明中应用了多个选择器时，每个选择器独占一行。
- 在规则声明的左大括号 { 前加上一个空格。
- 在属性的冒号 : 后面加上一个空格，前面不加空格。
- 规则声明的右大括号 } 独占一行。
- 规则声明之间用空行分隔开。
 
 bad
```
.avatar{
    border-radius:50%;
    border:2px solid white; }
.no, .nope, .not_good {
    // ...
}
#lol-no {
  // ...
}
```
 good
```
.avatar {
  border-radius: 50%;
  border: 2px solid white;
}

.one,
.selector,
.per-line {
  // ...
}
```

## 4,sass属性声明的顺序
 
@include 声明在一般属性之后再引用，增加可读性。 如果@include后面还有嵌套的话，用空行隔开
 bad
 ```
.btn-green {
    background: green;
    @include transition(background 0.5s ease);
    font-weight: bold;
    .icon {
      margin-right: 10px;
    }
  }
```
 good
 ```
.btn-green {
    background: green;
    font-weight: bold;
    @include transition(background 0.5s ease);

    .icon {
      margin-right: 10px;
    }
  }
```
  ### 变量
变量名应使用破折号（例如 $my-variable）代替 camelCased 和 snake_cased 风格。对于仅用在当前文件的变量，可以在变量名之前添加下划线前缀（例如 $_my-variable）。  

  ### Mixins
为了让代码遵循 DRY 原则（Don't Repeat Yourself）、增强清晰性或抽象化复杂性，应该使用 mixin，这与那些命名良好的函数的作用是异曲同工的。虽然 mixin 可以不接收参数，但要注意，假如你不压缩负载（比如通过 gzip），这样会导致最终的样式包含不必要的代码重复。  

  ### @extend

应避免使用 @extend 指令，因为它并不直观，而且具有潜在风险，特别是用在嵌套选择器的时候。即便是在顶层占位符选择器使用扩展，如果选择器的顺序最终会改变，也可能会导致问题。（比如，如果它们存在于其他文件，而加载顺序发生了变化）。其实，使用 @extend 所获得的大部分优化效果，gzip 压缩已经帮助你做到了，因此你只需要通过 mixin 让样式表更符合 DRY 原则就足够了。