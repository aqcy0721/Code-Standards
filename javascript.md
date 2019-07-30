
# JavaScript编码规范

#### 1. 变量命名
代码大全》这本书里面有一章是专门讲变量命名的，这里结合这本书的建议做说明。总地来说，变量名要准确完整地描述该变量所表述的事物，具体来说：
##### （1）变量名不应以短巧为荣
<table>

<tbody>

<tr>

<td>不好的变量名</td>

<td>好的变量名</td>

</tr>

<tr>

<td>inp</td>

<td>input, priceInput</td>

</tr>

<tr>

<td>day1, day2, param1</td>

<td>today, tomorrow</td>

</tr>

<tr>

<td>id</td>

<td>userId, orderId</td>

</tr>

<tr>

<td>obj</td>

<td>orderData, houseInfos</td>

</tr>

<tr>

<td>tId</td>

<td>removeMsgTimerId</td>

</tr>

<tr>

<td>handler</td>

<td>submitHandler, searchHandler</td>

</tr>

</tbody>

</table>
左边的变量名都不太清楚，代码的扩展性不好，一旦代码需要加功能的话，就容易出现obj1、obj2、obj3这种很抽象的命名方式。所以一开始就要把变量的名字起得真实有意义，不要搞一些很短很通用的名字。当然变量名取得太长也不好，如maximumNumberOfTeamMembers.

##### （2）变量名不要使用计算机术语
变量名应直指问题领域，来源于现实世界，而不是计算机世界，例如取了texareaData之类的名字，应该取一个和业务相关的名字，如leaveMsg.

##### （3）变量名的对仗要明确
如up/down、begin/end、opened/closed、visible/invisible、scource/target，对仗明确可以让人很清楚地知道两个变量的意义和用途。

##### （4）警惕临时变量
有些喜欢取temp和obj之类的变量，如果这种临时变量在两行代码内就用完了，接下来的代码就不会再用了，还是可以接受的，如交换数组的两个元素。但是有些人取了个temp，接下来十几行代码都用到了这个temp，这个就让人很困惑了。所以应该尽量少用temp类的变量，如下代码：


```
var temp = 10;
var leftPosition = currentPosition + temp，
    topPosition = currentPosition - temp;
```
应改成：
```
var adjustSpace = 10;
var leftPosition = currentPosition + adjustSpace，
     topPosition = currentPosition - adjustSpace;
```
##### （5）变量名使用正确的语法

不要使用中文拼音，如shijianchuo应改成timestamp，如果是复数的话加s，或者加上List，如orderList、menuItems，而过去式的加上ed，如updated/found等，如果正在进行的加上ing，如calling.

#### 2. 声明变量时要赋值
如下声明三个变量：
```
var registerForm,
     question,
     calculateResult;
 ```

以上绝对是合法JS语法，但是这三个变量的用途会让人比较困惑，特别是中间第二个question，问题是什么。但是当你把上面的变量赋一个初始值的时候：

```
var registerForm = null,
     question = "",
     calculateResult = 0;
```

就让人豁然开朗了，原来question是一个问题的字符串，而result是一个数字，form是一个对象。这也有利于JS解释器提前做一些优化处理，不用等到使用的时候才知道这些变量是什么类型的。

#### 3. 不要给变量赋值undefined
undefined表示一个变量未定义，你定义了一个变量又说它未定义本身就很奇怪。这可能会造成的问题是使用上的歧义，因为我们经常使用undefined来判断变量有没有定义

如果要赋值应该要赋空值，如对象赋值为null，数字赋值为0，字符串赋值为空字符，那你可能会说0也是一个正常的数字，如果赋值为0会导致我误认为它是一个正常的数据，那怎么办呢？如果你的数字都是非负数，那么可以把初始值置为-1，实在不行就置成NaN.

函数的返回值也不要显式地return undefined.
#### 4. 使用=== 代替 ==
== 会带上类型转换，这和上面一样的，我们要用强类型的风格写代码，所以不要使用==，如果有类型转换自己做类型转换，不要让别人去猜这里面有类型转换，使用==会有一些比较奇怪的结果：
```
null == undefined          //true
'' == '0'                  //false
0  == ''                   //true
0  == '0'                  //true
' \t\r\n ' == 0            //true
new String("abc") == "abc" //true
new Boolean(true) == true  //true
true == 1                  //true
```

#### 5. 不要让代码暴露在全局作用域下运行
一个原因是在全局作用域下，变量的查找时间会更长，第二个原因是污染全局作用域，有时候会造成一些意想不到的结果，如下：
```
var name = "hi boy";
console.log(window.name);
```
定义了一个变量，但是刚好不巧window.name是本来有这个属性，这个属性通常用来跨域传递数据。如果你设置了name这个变量，就把全局的window.name给覆盖了。
#### 6. let/var/const的使用
ES6新增了let/const定义变量，使用let有一些好处，如：
##### （1）避免变量重复定义
重复定义会报错, var则不会
##### （2）for循环的变量作用域是独立的
let作用域限制在被声明处的代码块内

而const适合于给常量起个名字, 用于定义其它一些不需要修改的变量，变量值不能被修改, 被修改会报错。  
**注1**: 部分浏览器对es6语法支持较差, 应使用babel插件对js代码编译使用  
**注2**: 常量声明const与 let 声明一样，都是块级声明
。  
**注3**: 注意 let 或 const 会像var一样屏蔽老变量, 但不会被绑定在window对象上, 如果需要绑定, 则用var

#### 7. 多写注释
这个和CSS规范类似：

##### （1）文件顶部的注释，包括描述、作者、更新

```
/*
 * @file listing-detail.js
 * @description 房源详情页的JS主文件，处理轮播、房贷计算器、约看房等逻辑
 * @author yincheng.li
 * @update (yincheng.li 2017/8/19)
 */
```
##### （2）函数的注释

```
/*
 * 和搜索界面展示有关的处理逻辑
 * @namespace
 */

var searchWinHandler = {
    /*
     * 初始化驱动函数
     * 
     * @param {bool} realTimeSearch 是否需要进行实时搜索
     * @param {HTMLFormElement} form 搜索表单DOM元素
     *
     */
    init(realTimeSearch, HTMLFormElement){

    }

    /*
     * 搜索条件展示点击X按钮的处理函数
     *
     * @param {object} jquery的点击事件event
     * @trigger 会触发search按钮的点击事件，以触发搜索
     * @returns 无返回
     *
     * TODO 这里临时使用了一个全局变量的flag，这种实现方式不太好
     * 虽然比较方便
     */              
    closeFilterSpan(event){

    }

};
```

上面的@auhor @return都是注释标签，其它常用的注释标签还有：

```
/*
@class 表示一个类
@constructor 构造函数
@deprecated 被弃用
@global 全局的变量
@namespace 具有命名空间作用的object，如$.fn.remove，$.fn.append，$和fn就是一个namespace，而fn是$的子命名空间
@this 这里的this指向哪里
@throws 在这个函数里面可能会抛出什么异常
@version 当前版本
*/
```

**注**: vscode上可使用插件 `Add jsdoc comments` 对函数代码做快捷注释  

#### 8. jQuery编码规范

##### （1）使用closest代替parent
尽量不要使用parent去获取DOM元素，如下代码：

```
var $activeRows = $this.parent().parent().children(".active");
```
这样的代码扩展性不好，一旦DOM结构发生改变，这里的逻辑分分钟会挂，如某天你可能会套了个div用来清除浮动，但是没想到导致有个按钮点不了了就坑爹了。

应该用closest，如：

```
var $activeRows = $this.closest(".order-list").find(".active");
```
##### （2）选择器的性能问题

```
$(".page ul").addClass("shown");
$(".page .page-number").text(number);
$(".page .page-next").removeClass("active");
```
上面的代码做了三个全局查找，其实可以优化一下：

```
var $page = $(".page");
$page.find("ul").addClass("shown");
$page.find(".page-number").text(number);
$page.find(".page-next").removeClass("active");
```
先做一个全局查找，后续的查DOM都缩小到$page的范围，$page的节点只有几十个，在几个里面找就比在document几百几千个节点里面查找要快多了. 日常写代码中, 可将一段功能块的代码中用到较多的jq dom元素声明为变量复用, 而不是每次都用对应jq选择器进行选择, 可提高jq运行性能

##### （3）对DOM节点较少的不要使用委托绑定
jq事件绑定分为直接绑定和委托绑定, 后者又叫动态绑定.  
例如说一个表单只有几个input元素，然后你给input加了个委托到form上面，甚至有时候是body上面，由于事件冒泡导致在form上或者在页面上的所有操作都会冒泡到form/body上，即使操作的不是目标元素，这样jQuery就会收到在body上的事件，然后再判断处理所有的操作的目标元素是不是你指定的那个，如果是再触发你绑的回调函数。**特别是像mousemove触发得频繁的事件都需要执行**。所以如果元素比较少或者不需要动态增删的那种就不要使用冒泡了，直接绑在对应的多个元素就好了。可优化jq性能

#### 9.  对于常用的属性进行缓存
如下代码，频繁地使用了window.location这个属性：

```
let webLink = window.location.protocol + window.location.hostname;
if(openType === "needtoTouch"){
    webLink += "/admin/lead/list/page" + 
             window.location.search.replace(/openType=needToTouch(&?)/, "") + 
             window.location.hash;
}
```
可以先把它缓存一下，加快变量作用域查找：

```
let location = window.location;
let webLink = location.protocol + location.hostname;
if(openType === "needtoTouch"){
    webLink += "/admin/lead/list/page" +
                location.search.replace(/openType=needToTouch(&?)/, "") +       
                location.hash;
}
```
当把location变成一个局部变量之后，它的查找时间将明显快于全局变量。你可能会说就算再快这点时间对于用户来说还是没有区别的吧，但是这是做为一名程序员的追求，以及可以让代码更简洁。
#### 10. 尽量不要在JS里面写CSS
尽量避免在js里直接修改css样式:

```
$menuItem.css("color", "#ccc");
```
因为首先出代码出问题难以定位, 其次如果想修改多个样式, 的话, 扩展起来比较麻烦, 会让js代码看起来比较臃肿, 最后就是, 复用性差.
最佳实践是通过类名控制:

```
//变成选中态
$menuItem.addClass("selected");
//变成非选中态
$menuItem.removeClass("selected");
```
将所要修改的样式使用状态类名(selected, on等)集中管理

#### 11. 在必要的地方添加非空判断
添加非空判断可以提高代码的稳健性，如下代码：

```
//弹框时显示other monthly charge
showOtherMonthlyCharge: function(otherCharges, $dialog){
    if(!otherCharges || !otherCharges.length){
        return;
    }   
}
```
如果传的为空就不用处理，有时候你可能要抛个异常，告诉调用者。对一些比较重要的地方可能还要添加类型检验。后端传的数据要确保会有那个属性，如果不确定也要添加非空判断。如果调了第三方的API，添加出错处理也很重要，因为你不能确保第三方API一定能正常工作，在一些你觉得可能会挂的地方做处理，如请求可能会超时，或者返回了undefined的异常结果，这种多使用一般能够发现。

#### 12. 分号规范
JS里面的表达式是可以不用分号结尾，例如Zepto的源码几乎没看到一个分号，但是我们还是提倡要每个句子后面都要加上分号，这样不容易出错。

#### 13. 注意返回false的变量
有几个值在if判断里面都返回false：0、false、””、undefined、null、NaN都是false，所以判断一个数组有没有元素可以这么写：

```
if (array.length) {}
```
而不用写成：


```
if (array.length !== 0) {}
```
判断一个字符串是不是空可以写成：


```
if (str) {}
```
但是判断一个变量有没有定义还是要写成：


```
if (typeof foo !== “undefined”) {}
```
因为如果直接if变量的话，上面的几个可能取值都将认为是没定义。

#### 14. 使用Object.assgin简化数据赋值

如下代码，在发请求之前，经常需要获取表单的值，然后去修改和添加老数据提交：


```
var orderData = {
    id: 123,
    price: 500
}

orderData.price = 600;
orderData.discount = 15;
orderData.manageFee = 100;
```
其实有种更优雅的方式那就是使用Object.assign：

```
var setOrderData = {
    price: 600,
    discount: 15,
    manageFee: 100
}

Object.assgin(orderData, setOrderData);
```
使用这个的好处是可以弄一个setOrderData的Object，写成大括号的形式，而不用一个个去赋值，写起来和看起来都比较累。最后再assign一下赋值给原先的Object就可以了。

#### 15. 保持复用模块的观念
当你一个函数要写得很长的时候，例如两、三百行，这个时候你考虑把这个大函数给拆了，拆成几个小函数，然后让主函数的逻辑变得清晰简洁，而每个小函数的功能单一独立，使用者只需要管输入输出，而不需要关心内部是怎么运行的。如下在地图里面处理用户点击的处理函数：

```
handleMouseClick(latLng, ajax = true) {
    var path = this.path;
    // 这里调了一个closeToFirstPoint的函数判断点击位置是否接近第一个点
    if(path.length >= 2 && ajax && this.closeToFirstPoint(latLng)){
        // 如果是的话调closePath关闭路径
        this.closePath(ajax);
        return;
    }
    path.push({lat: latLng.lat(), lng: latLng.lng()});
    // 调画点的函数
    this.drawPoint(latLng);
    // 调画线的函数
    this.drawSolidLine();
    // 调画多边形背景的函数
    this.drawPolygonMask();
    this.lastMoveLine && this.lastMoveLine.setMap(null);
    this.$drawTip.hide();
}

```
上面拆成了很多个小函数，如画点的drawPoint函数，使用这个函数只需要关心给它一个当前点的经纬度就可以了，它就帮你画一个点。在函数之上又可以继续抽象，如把这个画图功能的模块写成一个DrawTool的类，这个类负责整个画图的功能，使用者只需要实例化一个对象，然后调一下init，传一些参数就好了。先抽成不同的函数，每个函数负责一小块，相似的函数聚集在一起形成一个模块，几个模块的相互调用又形成一个插件。

##### [建议] 对于相同变量或表达式的多值条件，用 `switch` 代替 `if`。

示例：

```javascript
// good
switch (typeof variable) {
    case 'object':
        // ......
        break;
    case 'number':
    case 'boolean':
    case 'string':
        // ......
        break;
}

// bad
var type = typeof variable;
if (type === 'object') {
    // ......
} 
else if (type === 'number' || type === 'boolean' || type === 'string') {
    // ......
}
```

##### [建议] 如果函数或全局中的 `else` 块后没有任何语句，可以删除 `else`。

示例：

```javascript
// good
function getName() {
    if (name) {
        return name;
    }

    return 'unnamed';
}

// bad
function getName() {
    if (name) {
        return name;
    }
    else {
        return 'unnamed';
    }
}
```

##### [建议] `number` 去除小数点，使用 `Math.floor / Math.round / Math.ceil`，不使用 `parseInt`。

示例：

```javascript
// good
var num = 3.14;
Math.ceil(num);

// bad
var num = 3.14;
parseInt(num, 10);
```

##### [强制] 遍历数组不使用 `for in`。

解释：

数组对象可能存在数字以外的属性, 这种情况下 for in 不会得到正确结果.

示例：

```javascript
var arr = ['a', 'b', 'c'];
arr.other = 'other things'; // 这里仅作演示, 实际中应使用Object类型

// 正确的遍历方式
for (var i = 0, len = arr.length; i < len; i++) {
    console.log(i);
}

// 错误的遍历方式
for (i in arr) {
    console.log(i);
}
```
