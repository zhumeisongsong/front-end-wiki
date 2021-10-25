组件划分
另一方面，组件划分也是一部分，一个项目划分多少页面，划分多少复用组件，如何更高效的组织它们，它们的api怎么定，场景是否都能满足，每个人写一套别人已经写好的东西，既浪费时间又不能提高，而且还不能集中精力去做一个精美的组件出来，后期使用和维护也有很大的问题，而这个正好是我目前的重点工作。
【html: 全体】
■_Html.pugとい名前はNG
まず概念として
Html > layoutであって、
lay out　> Htmlではない
また、layout/_Html..pugと見たときこれは名前が直感的ではないの、名前から役割が理解できません

■scriptの役割がわかりません
直ガキ自体を否定するつもり無いです、ただこちらの目的がなにが理解できていません
なので、別ファイル　or コメントを残しscriptの目的がわかるようにしてください

■`console.warn(“将根据已有的meta标签来设置缩放比例“)`このようなコンソールがリリース版には出力されないようしてください
これは、海外に発注するときに特に考慮してもらいたです
クライアント目線から考えたときに、consoleでわけのわからん言語が出力されたら不安になると思います。


■faviconが日本放題のものを使っています
これはとてもNGなので、意識をかえてください
仮に、クライント目線で考えたら、別のサービスのファビコンがはいってたいたら、会社のレベルを疑われます。


■html(lang=“zh-CN”)はなぜですか？


■各ページの構造の粒度が揃っていません
例、htmlの粒度を揃えてください。ちなみ、自分はどちらもclass名が良くないと思います

・tg.pug


```.tg
  .banner
  .scroll
    .worb-content```

・color.pug
  ```.color-wrap.scroll
    .banner
    .container```

■出力後のhtmlとurl構造が美しくないです
http://localhost:3000/webd/webd.html
のように、webd/webd.htmlだと、
・そもそも美しきない
・仮にback endとのつなぎを考えたときに、無駄な工数を発生させそう

■jsはminしているので、cssはminしていないのはなぜですか？

■sectionタグをもっと使用してください
■使用section跟UL.list标签


【css: 全体】
■common.scss
これは個人の好き好きだと思いますが、commonとい名前は避けたいです
理由といて、common = 共通、共同をおり、例えば、全ページで共有で使用しているheaderのスタイルなどを別ページ記入することと矛盾強いるように思えるからです
commonと使いたくなる気持ちもりかいできますが、commonより矛盾なく具体的な命名をしたいと思っています

■グローバルで、containerにスタイルの定義するのはよくありません
今回container問のは、至るモジュールであまりにリスキーだと思います

.container {
 max-width: map_get($global-width, pc);
 height: 100%;
 margin: 0 auto;
 padding: 0 map_get($global-padding, container);
}

■$global-paddingとい名前は変えたいです
$global-paddingだとpadding以外で、同様のUIでpaddingを取るときに、矛盾が生じます
そのため、$global-spaceの方がいいと思います。

■variable.scssのコメントが気になります
$global-colorという変数名がすでに、役割を説明敷いているので、あえてcommon colorといコメントは必要ないと思います




【header】
html
■headerの下にあるので、.headerとあるのはなぜですか？
headerタグにそのまま、.headerとつけるのではだめでしょか？
また、bannerText.pugのときは、containerの階層が違っています
なぜ、違っていますか？

■.headerはjustify-content: space-betweenを使わず、h1にflex grow:1がよいと思います
現在は
ロゴ menuという２つですが、３つに増えた場合、space-betweenだと余計な調節を生みます
例 ロゴ 検索　menu

■3つラインの間隔が均等になっていません

■x時のスタイルが崩れている

【footer】
■footerの下にあるので、.footerとあるのはなぜですか？
footerタグにそのまま、.footerとつけるのではだめでしょか？
また、bannerText.pugのときは、containerの階層が違っています
なぜ、違っていますか？

■copyright-wrapはなぜwrapする必要がありますか？

■footerのmax widthが間違っている





【html: bannerText.pug】
■bannerTextのTextという名前がは良くないと思います
banner : 役割
Text　 : 構成要素
という分けです。
今後追加を考えbannerTextとい構成であれば、banner_defaulとかのほうが意味が良いと思います
また、デザインとのコミュニケーションもこちらのほうがよいうかと思います。

■.bannerを_bannerText.pug内に含んでいないのではなぜでしょうか？

■class名の概念が揃っていいません
containerとmainはそれぞれどういう意図がなって命名していますか？


■.bannerのbackgroungd imageはinnerのstyleとしてかいてもかもれしれません


【tg】
■省略形はやめてください
tg,worbなど直感的に何を指しているのかわかりません

■page classの命名
現状あ.tgとう命名というクラスwrappしていますが、pageなど、何かしらのpre flexをつけて、重グクが起きないよにしてください
例えばpage_tgなど

■page classの位置
```body
 .header
 page_class
 .foooter```
という構成ですが、scssを一つのcssに待てめている状況下では、各ページ側から、headerのスタイル変更するこ考慮し↓のほうがいいです
```body.page_class
 .header
 .page_content
 .foooter```

■styleの影響範囲を考慮し、設計を行ってください

.tg {
 .item
}
となっていますが、.itemページにかからわず、多くのモジュールで使っています
この書き方だと、他のモジュールをこのページで流用した際に、影響をうけます
そのため
.tg {
 .module.name {
  > .item
 }
}
などように影響を抑えるようにしてください





【総括】
■他人が見ること考慮していない
例えば、srcipt部分など、innerでかく、別ファイルかどうかなどはどっちでもいいです
それ以上に、第三者にたいして全くの配慮がないことを問題です
他人がみても理解できるかを心がけて、ソースコードを記入してください

■ソースコードを流用するときは、削除スべきものはしっかりち削除してください

■全体として、フラクタル構造を意識して、設計を多なってください





是否合格 -> 测试 -> 提交代码

项目coding统一临时标准
css coding format
所有命名小写字母、数字，并用中划线组成
标签属性值用("")
img 标签必须要有alt属性
标签中最好不要用style
遵循语义化标签使用规则，有利于SEO
尽量不缩写，除非一看就明白的单词
文件必须用UTF-8编码
css 嵌套最好不要超过4层，如若超过用名称前面加域，并提出来
ID 用驼峰法命名
每一条规则的大括号 { 前添加空格，结尾的{ 必须单独一行
规则与规则之间空行，规则内部不空行
链接的样式请严格按照如下顺序添加： a:link -> a:visited -> a:hover -> a:active
每个声明结束都应该带一个分号，不管是不是最后一个声明
合并margin、padding、border的-left/-top/-right/-bottom的设置
如果可以，颜色尽量用三位字符表示，例如#AABBCC写成#ABC
字体最好用偶数大小
在保持代码解耦的前提下，尽量合并重复的样式
选择器应该在满足功能的基础上尽量简短，减少选择器嵌套，查询消耗。但是一定要避免覆盖全局样式设置
字体值大小小于1时省略小数点前面的0，如：bad->font-size: 0.8rem, good->font-size: .8rem
** css 布局命名统一 **

*-wrap 表示外部布局块
header 用于最外层头部header
nav 导航条
*-content 表示内容
footer 用于外层footer
*-main 用于主要内容
*-row 表示行
*-col 表示列
*-menu 菜单
*-submenu 子菜单
*-sidebar 侧边栏
*-title 标题
以下可选常用命名： page、wrap、layout、header(head)、footer、 content(cont)、menu、nav、main、submain、sidebar(side)、logo、banner、 title(tit)、popo(pop)、icon、note、btn、txt、iblock、window(win)、tips等
** css 其他规范 **

不要轻易改动全站级CSS和通用CSS库。改动后，要经过全面测试
尽量不要在CSS中使用!important
层级(z-index)必须清晰明确，页面弹窗、气泡为最高级（最高级为999），不同弹窗气泡之间可在三位数之间调整；普通区块为10-90内10的倍数；区块展开、弹出为当前父层级上个位增加，禁止层级间盲目攀比
三级页面标准： A级－交互和视觉完全符全设计的要求 B级－视觉上允许有所差异，但不破坏页面的整体效果 C级－可忽略设计上的细节，但不防碍使用
前端管理规范建议
一定要有前端leader，并且需要让leader review 每一次项目成员提交的代码，而不只是看实际的效果是否合格，不合格的代码（js, css, html）都需要返回去重写。保证项目代码的干净、格式统一和最优状态
前端项目需要增加项目leader review code 的时间。项目流程：拿到设计图 -> 分析需求 -> 搭建框架 -> 分配工作 -> 检查代码

