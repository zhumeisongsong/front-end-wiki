# 测试金字塔 Test Pyramid 

## ■ 定义 Definition
前端测试金字塔提供了一个前端测试内容的架构规范。
The front-end test pyramid is a representation of how a front end test suite should be structured.

由三方面的测试内容构成：基本覆盖的````单元测试````、页面的````快照测试````和少量的````端对端````测试。The ideal test suite is comprised of ````unit tests````, some ````snapshot tests````, and a few ````end to end (e2e) tests````.

根据它定义了前端的````测试范围````及````合格条件````。

![test pyramid](/assets/images/test-pyramid.png)

<a name="table-of-contents"></a>

## 目录 Table of Contents

  1. [测试范围](#definition)
  1. [合格条件](#condition)

<a name="definition"></a>
## 测试范围 Test range


<a name="condition"></a>


## 单元测试 Unit tests

#### 方法返回的值正确
Functions return the correct result.

> 工具 Tool

Jest.js -- unit test case

> e.g. 

    日期格式化：Format time 
     
    全角字符转半角字符：Format DBC to SBC
      
#### 方法调用后，组件行为改变符合预期

Trigger actions on the components and check that the components behave as expected.

> 工具 Tool

Jest.js -- unit test case

> e.g. 

    点赞的方法调用后，点赞的样式改变
     
    手机菜单按钮点击后，菜单出现

### Pass standard

· 测试代码(Should)或手动测试(Must)；

· 定义的全部方法返回值正确(Should)；

· 方法调用后，组件的样式改变符合预期(Should)。


## 快照测试 Snapshot tests


#### 页面元素是否正确渲染

对比设计图或画面定义书


#### 测试多浏览器

> 工具 Tool

BrowserStack https://www.browserstack.com/

> 常规规范 Normal rule

Chrome / Safari / FF / IE11 / Android 5 / IOS 9

#### 响应式页面测试

> 工具 Tool

浏览器的开发者工具 /
BrowserStack https://www.browserstack.com/

> 常规规范 Normal rule
 
````1200 / 768 / 320```` 级别终端

#### 像素对比

> 工具 Tool

PerfectPixel (Chrome plugin)    

PhantomCSS https://github.com/HuddleEng/PhantomCSS (npm package)


### 合格标准 Pass standard

· 页面内容符合设计图或者画面定义书(Must);

· 响应式适配美观(should);

· 要求适配的浏览器没有样式错乱(Must);

· UI设计图1px高度还原或者与画面定义书式样一致（should）。


## 端对端测试 End to end tests (e2e)



#### 交互事件是否响应正确，ajax是否请求发出正常

> 工具 Tool

Jest.js / NightWatch

> e.g. 

    表单必填项是否填写完整

    表单input输入项目错误提示是否符合预期

    点击表单提交按钮，请求是否正常携带参数，ajax返回是否显示正常
    
    未登录时，浏览器Url访问需要登录权限的页面是否跳转登录页面


### 合格标准 Pass standard

· 画面定义书定义的功能正确实现；

· 稳定功能块的e2e测试代码覆盖(50%)或手动测试通过；

· 正常流程的e2e测试代码覆盖(50%)或手动测试通过；

· 异常处理的手动测试通过。

**[⬆ 返回目录](#table-of-contents)**


## References

https://medium.freecodecamp.org/the-front-end-test-pyramid-rethink-your-testing-3b343c2bca51
https://www.oschina.net/translate/the-front-end-test-pyramid-rethink-your-testing