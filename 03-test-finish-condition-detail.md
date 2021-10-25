# 单体测试完成条件--详细

<a name="table-of-contents"></a>
## 目录

  1. [式样准确 must](#style)
  1. [效果完整 must](#effect)
  1. [定义的方法工作正常 must](#function)
  1. [遵守普遍规范 must](#common)

<a name="style"></a>
## 式样准确

#### ■高精度还原设计图 
+ 1px

#### ■页面各section比例符合设计期待

#### ■多浏览器测试显示正常
- [ ] Chrome 
- [ ] Safari
- [ ] IE 11 / edge  （window10）
- [ ] Android 4.4.2
  - [ ] Hongmi Android 7
  - [ ] Honor 6A Android 7
  - [ ] Sony 4.4.2  
- [ ] IOS 10 + 
  - [ ] IPhone SE
  - [ ] IPhone 6/7/8
  - [ ] IPhone 6/7/8 plus
  - [ ] IPhone X
  - [ ] IPad
  
#### ■响应式适配符合设计期待或合理
+ 浏览拖拉边框改变window宽高显示正常
+ 手机旋转屏幕显示正常

#### ■Background-image/Image正确使用 更换图片后和设计效果表现一致

#### ■Font符合设计，同等级font表现一致
+ family
+ size 
+ weight
+ color
+ align

#### ■Color使用符合设计，同类对象color统一
+ font color
+ background color
+ wrapper-cover color

#### ■Border样式符合设计或统一，同类对象border式样统一


#### ■Form类式样符合设计或统一
    管理画面统一的规范参考：https://ant.design/

+ button
  + height
  + radius
  + min-width
  + width：100%留padding
  
+ input/textarea/checkbox/radio
  + height
  + radius
  
+ select
  + open/close样式
  + 点击外部收起

+ 报错信息位置，样式符合设计或统一


#### ■Feedback类出现条件和式样统一
    各个类对应的表现参考：https://ant.design/
+ alert
+ modal
+ message
+ Progress
+ notification

**[⬆Top](#table-of-contents)**



<a name="effect"></a>
## 效果完整

#### ■Hover式样和动画符合设计或统一
+ button 
+ a href
    
#### ■Active式样和动画符合设计或统一
+ header menu item
+ breadcrumb 

#### ■Form类 focus/blur/error/disable式样完整且统一
  

#### ■Animation符合设计或统一
    效果 速度
+ hover
+ active
+ scroll
+ menu

**[⬆Top](#table-of-contents)**



<a name="function"></a>
## 定义的方法工作正常

#### ■函数输入输出符合预期
+ params
+ init value
+ computed value

#### ■绑定事件正确
+ 绑定成功
+ 没有重复绑定
+ 及时解绑

#### ■ 方法调用正确
+ 调用时机
+ 调用次数

**[⬆Top](#table-of-contents)**



<a name="common"></a>
## 遵守普遍规范

#### ■语言设定正确
+ en-US / en
+ ja-JP / ja
+ zh-CN / zh

#### ■LOGO  加链接 加hover

#### ■Icon给大padding，确保点击范围
  + 注意SP难点中的问题


**[⬆Top](#table-of-contents)**