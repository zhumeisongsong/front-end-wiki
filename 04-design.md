# Design Check List

#### ■ Check List的内容，设计没有考虑全面的话，请提案

#### ■ Overview

- [ ] UI有没有矛盾
  - 业务上的矛盾：流程不合理/实现困难
  - 显示上的矛盾: 相同交互的式样不同
- [ ] 相同逻辑的交互是否一致：modal的弹出条件 / message的提示条件 等 
- [ ] 1920 设计图字体是否过大
- [ ] 404 / 500 / no-data / no-network等特殊页面有没有提供
- [ ] 用户登录与未登录的状态是否完整

#### ■ Responsive 

- [ ] 有没有单独的手机适配图提供
- [ ] 没有手机适配图PC的设计图是否常规方法可以适配成手机显示
- [ ] 注意2倍的SP设计图需要/2
- [ ] SP的菜单样式是否提供
- [ ] 320/375/768/1440等 尺寸屏幕的适配是否有问题
- [ ] Iphone X 底部bar对内容遮挡的特殊处理

#### ■ Layout

- [ ] 边距一定使用偶数 常用的左右边距一般为8/12/16px
- [ ] 内容边距容易分清属于谁的，有助于写页面的布局思路
- [ ] 管理画面遵守antd-design规范 使用8的倍数
- [ ] 同类组件间距应该一致

#### ■ Font

- [ ] 确认字体是否可以免费使用，特别是banner，logo
- [ ] 主、次、辅助、标题、展示等类别的字体样式在不同页面基本统一
- [ ] Font size符合最小限制：中文最小12px 日文/英文10px
- [ ] 多语言由于字数的不同，显示是否有问题

#### ■ Colors

- [ ] 同类颜色不同页面是否色号一致
- [ ] 字体颜色是否方便阅读

#### ■ Image

- [ ] 相同模块的图片显示尺寸 / 比例是否一致

#### ■ Button

- [ ] 是否提供不同的等级的按钮样式：primary / secondary / waring / disable / error
- [ ] 是否提供按钮不同的状态样式：hover / pressed / disabled / loading
- [ ] button height 统一

#### ■ A href

- [ ] 是否提供了 hover 样式
- [ ] 是否提供了 active 样式

#### ■ Border

- [ ] border 样式是否统一或可做共通
- [ ] border 的 radius 是否统一或可做共通
- [ ] SP 是否需要 0.5px 的 border

#### ■ 表单项目

- [ ] 提交流程是否完整
- [ ] 表单项目的验证错误提示样式是否提供
- [ ] 必填项的标记样式是否提供
- [ ] 提交成功的提示是否提供
- [ ] 提交错误的提示是否提供
- [ ] 表单项目 focus 样式是否提供
- [ ] input / button 等同类元素的样式是否一致

#### ■ effect

- [ ] 页面初期加载效果有没有提供
- [ ] scroll 时 header-nav 的效果是否有提供
- [ ] 列表 loading 效果有没有指定
- [ ] hover 效果是否有提供
- [ ] active 效果是否有提供
- [ ] animation 效果是否有提供

#### ■切图

- [ ] 提供的切图格式是否合理
- [ ] 提供的切图是否满足响应式布局需要
- [ ] 是否提供了模拟数据的图片切图
- [ ] 是否提供了所有的 icon 切图
  - 可以统一下载
  - 可以在当前位置下载
- [ ] 提供的图片是否压缩
  
#### ■ 细节
  
- [ ] 数据最多和最少的情况显示效果有没有指定
- [ ] 考虑设计图内容和实际内容的显示：字很多的情况/空的情况
- [ ] 图片是否需要使用 background 居中显示

## References

MonstarLab Chengdu UI Design Standard

https://ant.design/docs/spec/introduce-cn

https://mayvendev.com/blog/design-checklist-tips-and-examples
