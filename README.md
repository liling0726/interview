# interview
笔试提的总结
阿里笔试题
1、<style>
.a, .b, .c {position:relative;}
</style>
<div class="a">
  A
  <div class="c">C</div>
</div>
  <div class="b">B</div>
请补全上面代码中的css部分，让三个图层的层级为C>B>A
参考答案：z-index
2、怎么实现在一块画布上，画任意个圆不相交，且圆不能碰边界，要求做到时间和空间的平衡
<!DOCTYPE HTML>
<html>
<body>
<canvas id="myCanvas" width="202" height="202" style="border:1px solid blue;">
</canvas>
<script type="text/javascript">

var r = 4;//半径定义5
var xp = 6;//第一圆的x坐标
var yp = 6;//第一个圆的y坐标
var canvas = document.getElementById("myCanvas");
var cxt=canvas.getContext("2d");
var wi = canvas.clientWidth;//画布宽度
var hi = canvas.clientHeight;//画布高度
var wnum = (parseInt(wi)-2)/10;//横向排列圆的数量
var hnum = (parseInt(hi)-2)/10;//纵向排列圆的数量
for(var h=0;h<hnum;h++){
yp = h*10+6;	 //重新计算圆心点的Y坐标
for(var w=0;w<wnum;w++){
xp = w*10+6;	 //重新计算圆心点的x坐标
drawCircle(xp,yp,r,cxt);
}
}

function drawCircle(xp,yp,r){	
cxt.fillStyle="#FF0000";
cxt.beginPath();
cxt.arc(xp,yp,r,0,Math.PI*2,true);
cxt.closePath();
cxt.fill();
}
</script></body>
<html>
3、用JS实现一个函数，来“判断一个字符串中出现次数最多的字符，并统计出这个次数”
  js：var str='asdaa';
var obj={};
for(var i=0,l=str.length,k;i<l;i++){
k=str.charAt(i);
if(obj[k]){
obj[k]++;
}else{
obj[k]=1;
}
}
var m=0;
var i=null;
for(var k in obj){
if(obj[k]>m){
m=obj[k];
i=k;
}
}
alert(i+':'+m);
4、有一个包含数据列表的页面，数据行数不确定。每一行数据都有一个删除按钮，单击删除按钮删除该列数据，请用JavaScript实现该功能。
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>无标题文档</title>
</head>

<body>
<table>
<tr>
<th>姓名</th>
<th>学号</th>
<th>删除</th>
</tr>
<tr>
<td>张杰0</td>
<td>201221213</td>
<td><button onclick="deleteTr(this)" >删除</button></td>
</tr>
<tr>
<td>张杰1</td>
<td>201221213</td>
<td><button onclick="deleteTr(this)" >删除</button></td>
</tr>
<tr>
<td>张杰2</td>
<td>201221213</td>
<td><button onclick="deleteTr(this)" >删除</button></td>
</tr><tr>
<td>张杰3</td>
<td>201221213</td>
<td><button onclick="deleteTr(this)" >删除</button></td>
</tr><tr>
<td>张杰4</td>
<td>201221213</td>
<td><button onclick="deleteTr(this)" >删除</button></td>
</tr>
<tr>
<td>张杰5</td>
<td>201221213</td>
<td><button onclick="deleteTr(this)" >删除</button></td>
</tr>
</table>
<script>
function deleteTr(e){
 e.parentNode.parentNode.remove(e.parentNode);
}
</script>
</body>
</html>

5、请你用多种方法实现一个iOS样式的开关
   Html：
<dl>
<dt>Animate background</dt>
<dd>
<label class="iosCheck">
<input type="checkbox">
<i></i>
</label>
</dd>
<dt>Blur Newsstand</dt>
<dd>
<label class="iosCheck">
<input type="checkbox" checked="checked">
<i></i>
</label>
</dd>
<dt>Pinch to close</dt>
<dd>
<label class="iosCheck blue">
<input type="checkbox">
<i></i>
</label>
</dd>
<dt>Blur folder icon</dt>
<dd>
<label class="iosCheck blue">
<input type="checkbox" checked="checked">
<i></i>
</label>
</dd>
<dl>
Css:
.iosCheck {
  /* Blue edition */
}
.iosCheck input {
  display: none;
}
.iosCheck i {
  display: inline-block;
  cursor: pointer;
  padding-right: 25px;
  transition: all ease 0.2s;
  -webkit-transition: all ease 0.2s;
  border-radius: 25px;
  box-shadow: inset 0 0 1px rgba(0, 0, 0, 0.5);
}
.iosCheck i:before {
  display: block;
  content: '';
  width: 25px;
  height: 25px;
  border-radius: 25px;
  background: white;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.5);
}
.iosCheck :checked + i {
  padding-right: 0;
  padding-left: 25px;
  background: #00e970;
  box-shadow: inset 0 0 1px rgba(0, 0, 0, 0.5), inset 0 0 40px #00e079;
  -webkit-box-shadow: inset 0 0 1px rgba(0, 0, 0, 0.5), inset 0 0 40px #00e079;
}
.iosCheck.blue :checked + i {
  background: #6cbff0;
  box-shadow: inset 0 0 1px rgba(0, 0, 0, 0.5), inset 0 0 40px #0093ea;
  -webkit-box-shadow: inset 0 0 1px rgba(0, 0, 0, 0.5), inset 0 0 40px #0093ea;
}
/* General styling */
body {
  font-family: 'Helvetica neue', Helvetica, Arial, sans-serif;
  width: 400px;
  margin: 0 auto;
}
dl {
  width: 370px;
}
dl:after {
  content: "";
  display: table;
  clear: both;
}
dt {
  width: 200px;
  height: 40px;
  float: left;
}
dd {
  float: left;
  width: 100px;
}
6、请向指定的DIV中添加100个span标签
     <div id=”container”></div>
参考：
（1）、使用fragment
（2）、html+
（3）、append
7、利用Nodejs的fs模块的，实现文件夹的深度优先遍历和广度优先遍历
  输入：文件夹路径
  输出：文件列表

8、下面代码希望在点击每段内容的时候给它加个灰色背景，可是下面这段代码好像没有满足需求，请帮忙修改下。
for(var i = 0; i < document.getElementsByTagName('p').length; i ++) {
var item = document.getElementsByTagName('p')[i];
(function(j) {
document.getElementsByTagName('p')[i].onclick = function() {
item.style.backgroundColor='#eee';
改为this

}
}(i))
}
9、使用语义化的 HTML 标签及css完成以下布局
•容器默认宽度320px，图片100*100
•hover 时容器宽度变为400px
•右侧文字宽度自适应，考虑模块化和扩展性        ????

参考：
<div id="container">
<img src="2.jpg" />
</div>
#container{
width:300px;
background:blue;
}
img{
height:100px;
width:100px;}
#container:hover{
width:400px;
}

10、为字符串实现一个render方法，实现下面的变量替换功能
var greeting = 'my name is ${name}, age ${age}';
var result = greeting.render({name: 'XiaoMing', age: 11});
console.log(result);  //my name is XiaoMing, age 11
答案：
String.prototype.render=function(obj){
var result=this;
for(var i in obj)
{
var name="\$\{"+i+"\}"

 result=result.replace(name,obj[i]);
}
return result;
} 
var greeting = 'my name is ${name}, age ${age}';
var result = greeting.render({name: 'XiaoMing', age: 11});
console.log(result);  //my name is XiaoMing, age 11
11、用js实现随机选取10–100之间的不同的10个数字，存入一个数组，并降序排序
var aArray = [
];
var i = 0;
for (i = 0; i < 10; i++) {
  randomNub();
}
aArray.sort(function (a, b) {
  return b - a
});
document.write(aArray)
function randomNub() {
  var nowNub = parseInt(Math.random() * 100);
  if (nowNub < 10) {
    randomNub();
    return;
  }
  for (var j = 0; j < aArray.length; j++) {
    if (nowNub == aArray[j]) {
      randomNub();
      return;
    }
  }
  aArray.push(nowNub);
}
12、实现jQuery的html方法
  $("#id").html("插入");
  ==>document.getElementById("id").innerHTML="插入";
  $("#id").html();
  ==>document.getElementById("id").innerHTML;
<div id="d1"></div>
<script>
function $(d) {return document.getElementById(d);}

$("d1").innerHTML = "xxx"
</script> 
13、编写一个javascript函数,可以在页面上异步的加载js,在加载结束后执行callback,并在IE和Chrome下都能执行.
function loadScript(url,callback){
//需要填写的内容
}
function loadScript(url, callback){
var script = document.createElement("script")
script.type = "text/javascript";
if (script.readyState){ //IE
script.onreadystatechange = function(){
if (script.readyState == "loaded" ||
script.readyState == "complete")
{
script.onreadystatechange = null;
callback();
}
};

网上的试题
1	var name = 'laruence';     
function echo()
 {         
  alert(name);   
 }      
function env()
 {
    var name = 'eve';         
    echo();   
}      

env();
答案：输出 laruence
2、
function test(xxx){
  alert(xxx);
  var xxx = 123; 
  function xxx(){  
  }
  alert(xxx); 
}
test(444);
答案：输出 function xxx(){}，123 
这主要考察了函数执行时初始化顺序：函数被执行时，首先创建执行环境（执行上下文），构建该 环境时，1.首先创建arguments变量，包含了传入的参数，2 .创建创建作用域链  ，3 。初始化变量，首先会初始化函数的形参表，值为arguments里面中对应的值，如果arguments中没有对应的值，则形参为undefined  ，4。初始化内部函数 ，5， 初始化函数内部的局部变量（undefined） 6. 最后当执行环境创建成功后，局部变量赋值 。
  因此，在执行test（444）时，xxx为形参，值为444；进入test()函数时，首先初始化function xxx(){}，此时xxx为function;接下来执行到alert(xxx)，输出function xxx{};向下执行到var xxx=123,此时xxx=123，alert（xxx），输出123.
3、
var func1={
    name:"a",
    test: function(){
     alert(this.name);
   }
 } 
  name="global";
  func1.test();
  func=func1.test();
  func();//firefox func is not function; google undefined  is not function;
  function func2(){
  var name="func2";  
  func();
}
 func2();
输出：a，a然后报错
4、if(!("a"  in  window)){
     var a =1;
}
 alert(a);

输出：undefined；
 
解析： 刚开始a 为undefined ,undefined in window 返回true ,所以它是进不了if()
5、var a=1,
         b=function a(x){
           x&&(--x);
             };
  alert(a);

输出：1 

解析： 方法a()的调用只能在function a(){}的内部调用，外部调用只能调用b(x);
6、function JSClass() {
            this.m_Text = 'division element';
            this.m_Element = document.createElement('DIV');
            this.m_Element.innerHTML = this.m_Text;

            this.m_Element.attachEvent('onclick', this.ToString);
        }

        JSClass.prototype.Render = function() {
            document.body.appendChild(this.m_Element);
        }

        JSClass.prototype.ToString = function() {
            alert(this.m_Text);
        };

        var jc = new JSClass();
        jc.Render();//添加渲染div元素
        jc.ToString(); //输出 division element

        //click添加的div元素division element会输出underfined，为什么？
//这时的EventHandler()方法中的this关键字，指示的对象是IE的window对象。
        //这是因为EventHandler只是一个普通的函数，对于attachEvent后，
        //脚本引擎对它的调用和div对象本身没有任何的关系。同时你可以再看看EventHandler的caller属性，
        //它是等于null的。如果我们要在这个方法中获得div对象引用，应该使用：this.event.srcElement。 

7、var obj = {
            i: "test",
            m: function() {
                alert(this.i); //指向obj对象 实例,输出值test 
                function B() {
                    alert(this.i); //输出值undefined
                    //调用B的实例是m，不是obj，所以this就是m
                    //m里面没有i，所以默认会加上一句var i；当然是underfined。
                }
                B(); 
            }
        }
        obj.m();
8、var obj = {
           i: "test",
           m: function() {
               alert(this.i); //指向obj对象 实例,输出值test 
               function B() {
                 var i=1;
                   alert(this.i); );//指向window对象,值undefined                     
                 
               }
               B();//B并不是window的方法，this为什么也指向window？？？？？？
           }
       }
       obj.m();


1、请实现，鼠标点击页面中的任意标签，

<script type="text/javascript">  

document.onclick=function(e){  

     var e=(e||event);  

     var o=e["target"]||e["srcElement"];  

     alert(o.tagName.toLowerCase());  

}  

</script> 

2请指出一下代码的性能问题，并经行优化。

 
var info="腾讯拍拍网（www.paipai.com）是腾讯旗下知名电子商务网站。";  

info +="拍拍网于2005年9月12日上线发布，";  
info +="2006年3月13日宣布正式运营，";  
info +="是目前国内第二大电子商务平台。";  
info=info.split(",");  
for(var i=0; i<info.length; i++)  {  
 alert(info[i]);  } 

这题初看纯属折腾，

因为后面要根据逗号分隔再alert每项，何不构造一个数组对象来存放文本内容，而要用个临时变量info才存放。
如

var info=["腾讯拍拍网（www.paipai.com）是腾讯旗下知名电子商务网站。","拍拍网于2005年9月12日上线发布，","2006年3月13日宣布正式运营，","是目前国内第二大电子商平台。"] 。
可是后来想如果是优化的话这个题目就出的没意义了。
仔细观察info这个变量，发现它每次都要自加字符串，如果字符串很大的又很多的话会非常影响性能的。对于js中的string类型，属于基本类型，因此一般情况下他们是存放在栈上的。如果字符串很大，info会每次变成一个很长的字符串，会很慢。
如果用引用类型数组来存放则好很多，如：
var temp=[];  

temp.push("腾讯拍拍网（www.paipai.com）是腾讯旗下知名电子商务网站。");  

//temp只是一个指向堆上数组的指针
temp.push("拍拍网于2005年9月12日上线发布，");   
temp.push("2006年3月13日宣布正式运营，");  
temp.push("是目前国内第二大电子商务平台。");  
temp.join("");  alert(temp); 最后一招
temp.join(“”)搞定。
对处理大字符串连接问题都可以采取这种思路。

3、请给出异步加载js方案，不少于两种。

异步加载方式：

 (1) defer，只支持IE 

(2) async：html5中script标签才有的属性

(3) 创建script，插入到DOM中，加载完毕后callBack
，见代码：

 
function loadScript(url, callback){  

   var script = document.createElement("script")  

   script.type = "text/javascript";  

   if (script.readyState){ //IE  

      script.onreadystatechange = function(){  

         if (script.readyState == "loaded" ||  

            script.readyState == "complete"){  

            script.onreadystatechange = null;  

            callback();  

         }  

      };  

   } else { //Others: Firefox, Safari, Chrome, and Opera  

      script.onload = function(){  

          callback();  

      };  

   }  

   script.src = url;  

   document.body.appendChild(script);  

} 

4 、请写出jQuery绑定事件的方法，不少于两种。

$("#obj").click(function(){});  

$("#obj").change(function(){});  
$("#obj").bind("click",function(){});  

$("#obj").live("submit",function(){}); 

5、请设计一套方案，用于确保页面中JS加载完全。

var n = document.createElement("script");  

n.type = "text/javascript";  

//以上省略部分代码

 //ie支持script的readystatechange属性
if(ua.ie){  
 n.onreadystatechange = function(){  

       var rs = this.readyState;  

       if('loaded' === rs || 'complete'===rs){  

           n.onreadystatechange = null;  

           f(id,url); //

回调函数
       }  

};  

//省略部分代码

//safari 3.x supports the load event for script nodes(DOM2)  

   n.addEventListener('load',function(){  

       f(id,url);  

   });  

//firefox and opera support onload(but not dom2 in ff) handlers for  

//script nodes. opera, but no ff, support the onload event for link  

//nodes.  

}else{  

   n.onload = function(){  

       f(id,url);  

   };  

} 

6 、请优化某网页的加载速度。

 

7 对string对象经行扩展，使其具有删除前后空格的方法。

String.prototype.trim =function(){  

   

    return this.replace(/(^\s*)|(\s*$)/g,'');  
} 

8 完成一个正则表达式，验证用户输入是否身份证号码。var Expression=/\d{17}[\d|X]|\d{15}/;  
var objExp=new RegExp(Expression);

9、
var name = 'laruence';     
function echo()
 {         
  alert(name);   
 }      
function env()
 {
    var name = 'eve';         
    echo();   
}      

env();
答案：输出 laruence

试题目录：
1.	HTML 部分
2.	CSS 部分
3.	JavaScript 部分
4.	其他问题
面试注意点：
面试题目： 根据你的等级和职位变化，入门级到专家级：范围↑、深度↑、方向↑。
题目类型： 技术视野、项目细节、理论知识题，算法题，开放性题，案例题。
进行追问： 可以确保问到你开始不懂或面试官开始不懂为止，这样可以大大延展题目的区分度和深度，知道你的实际能力。因为这种关联知识是长时期的学习，绝对不是临时记得住的。
回答问题再棒，面试官（可能是你的直接领导面试），会考虑我要不要这个人做我的同事？所以态度很重要。（感觉更像是相亲）
资深的工程师能把absolute和relative弄混，这样的人不要也罢，因为团队需要的你这个人具有可以依靠的才能（靠谱）。
试题大纲：
HTML&CSS：
    对Web标准的理解、浏览器内核差异、兼容性、hack、CSS基本功：布局、盒子模型、选择器优先级及使用、HTML5、CSS3、移动端适应
JavaScript：  
    数据类型、面向对象、继承、闭包、插件、作用域、跨域、原型链、模块化、自定义事件、内存泄漏、事件机制、异步装载回调、模板引擎、Nodejs、JSON、ajax等。
其他：
   HTTP、安全、正则、优化、重构、响应式、移动端、团队协作、可维护、SEO、UED、架构、职业生涯
web前端工程师知识点：
1、DOM结构 —— 两个节点之间可能存在哪些关系以及如何在节点之间任意移动。
2、DOM操作  ——如何添加、移除、移动、复制、创建和查找节点等。
3、事件    —— 如何使用事件，以及IE和标准DOM事件模型之间存在的差别。
4、XMLHttpRequest —— 这是什么、怎样完整地执行一次GET请求、怎样检测错误。
5、严格模式与混杂模式 —— 如何触发这两种模式，区分它们有何意义。
6、盒模型 —— 外边距、内边距和边框之间的关系，及IE8以下版本的浏览器中的盒模型
7、块级元素与行内元素 —— 怎么用CSS控制它们、以及如何合理的使用它们
8、浮动元素——怎么使用它们、它们有什么问题以及怎么解决这些问题。
9、HTML与XHTML——二者有什么区别，你觉得应该使用哪一个并说出理由。
10、JSON  —— 作用、用途、设计结构。
HTML
Doctype作用? 严格模式与混杂模式如何区分？它们有何意义?
（1）、<!DOCTYPE> 声明位于文档中的最前面，处于 <html> 标签之前。告知浏览器的解析器，       用什么文档类型 规范来解析这个文档。   （2）、严格模式的排版和 JS 运作模式是  以该浏览器支持的最高标准运行。  （3）、在混杂模式中，页面以宽松的向后兼容的方式显示。模拟老式浏览器的行为以防止站点无法工作。  （4）、DOCTYPE不存在或格式不正确会导致文档以混杂模式呈现。
行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？
（1）CSS规范规定，每个元素都有display属性，确定该元素的类型，每个元素都有默认的display值，   比如div默认display属性值为“block”，成为“块级”元素；   span默认display属性值为“inline”，是“行内”元素。    （2）行内元素有：a b span img input select strong（强调的语气）   块级元素有：div ul ol li dl dt dd h1 h2 h3 h4…p    （3）知名的空元素： <br> <hr> <img> <input> <link> <meta>  鲜为人知的是： <area> <base> <col> <command> <embed> <keygen> <param> <source> <track> <wbr>
link 和@import 的区别是？
（1）link属于XHTML标签，而@import是CSS提供的;  （2）页面被加载的时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载;  （3）import只在IE5以上才能识别，而link是XHTML标签，无兼容问题;  （4）link方式的样式的权重 高于@import的权重. 
浏览器的内核分别是什么?
 * IE浏览器的内核Trident、Mozilla的Gecko、Chrome的Blink（WebKit的分支）、Opera内核原为Presto，现为Blink；
常见兼容性问题？
* png24位的图片在iE6浏览器上出现背景，解决方案是做成PNG8.  * 浏览器默认的margin和padding不同。解决方案是加一个全局的*{margin:0;padding:0;}来统一。  * IE6双边距bug:块属性标签float后，又有横行的margin情况下，在ie6显示margin比设置的大。     浮动ie产生的双倍距离 #box{ float:left; width:10px; margin:0 0 0 100px;}    这种情况之下IE会产生20px的距离，解决方案是在float的标签样式控制中加入 ——_display:inline;将其转化为行内属性。(_这个符号只有ie6会识别)    渐进识别的方式，从总体中逐渐排除局部。     首先，巧妙的使用“\9”这一标记，将IE游览器从所有情况中分离出来。    接着，再次使用“+”将IE8和IE7、IE6分离开来，这样IE8已经独立识别。    css       .bb{        background-color:#f1ee18;/*所有识别*/       .background-color:#00deff\9; /*IE6、7、8识别*/       +background-color:#a200ff;/*IE6、7识别*/       _background-color:#1e0bd1;/*IE6识别*/        }   *  IE下,可以使用获取常规属性的方法来获取自定义属性,    也可以使用getAttribute()获取自定义属性;    Firefox下,只能使用getAttribute()获取自定义属性.     解决方法:统一通过getAttribute()获取自定义属性.  * IE下,even对象有x,y属性,但是没有pageX,pageY属性;    Firefox下,event对象有pageX,pageY属性,但是没有x,y属性.  * 解决方法：（条件注释）缺点是在IE浏览器下可能会增加额外的HTTP请求数。  * Chrome 中文界面下默认会将小于 12px 的文本强制按照 12px 显示,    可通过加入 CSS 属性 -webkit-text-size-adjust: none; 解决.  超链接访问过后hover样式就不出现了 被点击访问过的超链接样式不在具有hover和active了解决方法是改变CSS属性的排列顺序:L-V-H-A :  a:link {} a:visited {} a:hover {} a:active {}
html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML 和 HTML5？
* HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加。  * 绘画 canvas     用于媒介回放的 video 和 audio 元素    本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失；   sessionStorage 的数据在浏览器关闭后自动删除    语意化更好的内容元素，比如 article、footer、header、nav、section    表单控件，calendar、date、time、email、url、search     新的技术webworker, websockt, Geolocation  * 移除的元素  纯表现的元素：basefont，big，center，font, s，strike，tt，u；  对可用性产生负面影响的元素：frame，frameset，noframes；  支持HTML5新标签：  * IE8/IE7/IE6支持通过document.createElement方法产生的标签，   可以利用这一特性让这些浏览器支持HTML5新标签，    浏览器支持新标签后，还需要添加标签默认的样式：  * 当然最好的方式是直接使用成熟的框架、使用最多的是html5shim框架    <!--[if lt IE 9]>     <script> src="http://html5shim.googlecode.com/svn/trunk/html5.js"</script>     <![endif]-->  如何区分： DOCTYPE声明\新增的结构元素\功能元素
语义化的理解？
用正确的标签做正确的事情！ html语义化就是让页面的内容结构化，便于对浏览器、搜索引擎解析； 在没有样式CCS情况下也以一种文档格式显示，并且是容易阅读的。 搜索引擎的爬虫依赖于标记来确定上下文和各个关键字的权重，利于 SEO。 使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。
HTML5的离线储存？
localStorage    长期存储数据，浏览器关闭后数据不丢失； sessionStorage  数据在浏览器关闭后自动删除。
(写)描述一段语义的html代码吧。
（HTML5中新增加的很多标签（如：<article>、<nav>、<header>和<footer>等）  就是基于语义化设计原则）       < div id="header">      < h1>标题< /h1>      < h2>专注Web前端技术< /h2>      < /div>
iframe有那些缺点？
*iframe会阻塞主页面的Onload事件；  *iframe和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。 使用iframe之前需要考虑这两个缺点。如果需要使用iframe，最好是通过javascript 动态给iframe添加src属性值，这样可以可以绕开以上两个问题。
请描述一下 cookies，sessionStorage 和 localStorage 的区别？
cookie在浏览器和服务器间来回传递。 sessionStorage和localStorage不会 sessionStorage和localStorage的存储空间更大； sessionStorage和localStorage有更多丰富易用的接口； sessionStorage和localStorage各自独立的存储空间；
如何实现浏览器内多个标签页之间的通信? (阿里)
调用localstorge、cookies等本地存储方式
webSocket如何兼容低浏览器？(阿里)
Adobe Flash Socket 、 ActiveX HTMLFile (IE) 、 基于 multipart 编码发送 XHR 、 基于长轮询的 XHR
CSS
介绍一下CSS的盒子模型？
（1）有两种， IE 盒子模型、标准 W3C 盒子模型；IE的content部分包含了 border 和 pading;  （2）盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border).
CSS 选择符有哪些？哪些属性可以继承？优先级算法如何计算？ CSS3新增伪类有那些？
*   1.id选择器（ # myid）    2.类选择器（.myclassname）    3.标签选择器（div, h1, p）    4.相邻选择器（h1 + p）    5.子选择器（ul < li）    6.后代选择器（li a）    7.通配符选择器（ * ）    8.属性选择器（a[rel = "external"]）    9.伪类选择器（a: hover, li: nth - child） *   可继承的样式： font-size font-family color, UL LI DL DD DT; *   不可继承的样式：border padding margin width height ; *   优先级就近原则，同权重情况下样式定义最近者为准; *   载入样式以最后载入的定位为准;
优先级为:
   !important >  id > class > tag       important 比 内联优先级高
CSS3新增伪类举例：
p:first-of-type 选择属于其父元素的首个 <p> 元素的每个 <p> 元素。p:last-of-type  选择属于其父元素的最后 <p> 元素的每个 <p> 元素。p:only-of-type  选择属于其父元素唯一的 <p> 元素的每个 <p> 元素。p:only-child    选择属于其父元素的唯一子元素的每个 <p> 元素。p:nth-child(2)  选择属于其父元素的第二个子元素的每个 <p> 元素。:enabled  :disabled 控制表单控件的禁用状态。:checked        单选框或复选框被选中。
如何居中div？如何居中一个浮动元素？
给div设置一个宽度，然后添加margin:0 auto属性
div{     width:200px;     margin:0 auto;  }  
居中一个浮动元素
  确定容器的宽高 宽500 高 300 的层   设置层的外边距   .div {    Width:500px ; height:300px;//高度可以不设   Margin: -150px 0 0 -250px;   position:relative;相对定位   background-color:pink;//方便看效果   left:50%;   top:50%;} 
列出display的值，说明他们的作用。position的值， relative和absolute定位原点是？
  1.      block 象块类型元素一样显示。   none 缺省值。象行内元素类型一样显示。   inline-block 象行内元素一样显示，但其内容象块类型元素一样显示。   list-item 象块类型元素一样显示，并添加样式列表标记。    2.    *absolute          生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位。     *fixed （老IE不支持）         生成绝对定位的元素，相对于浏览器窗口进行定位。     *relative          生成相对定位的元素，相对于其正常位置进行定位。     * static  默认值。没有定位，元素出现在正常的流中   *（忽略 top, bottom, left, right z-index 声明）。    * inherit 规定从父元素继承 position 属性的值。
CSS3有哪些新特性？
  CSS3实现圆角（border-radius:8px），阴影（box-shadow:10px），   对文字加特效（text-shadow、），线性渐变（gradient），旋转（transform）   transform:rotate(9deg) scale(0.85,0.90) translate(0px,-30px) skew(-9deg,0deg);//旋转,缩放,定位,倾斜   增加了更多的CSS选择器  多背景 rgba 
一个满屏 品 字布局 如何设计?
经常遇到的CSS的兼容性有哪些？原因，解决方法是什么？
为什么要初始化CSS样式。
- 因为浏览器的兼容问题，不同浏览器对有些标签的默认值是不同的，如果没对CSS初始化往往会出现浏览器之间的页面显示差异。 - 当然，初始化样式会对SEO有一定的影响，但鱼和熊掌不可兼得，但力求影响最小的情况下初始化。  *最简单的初始化方法就是： * {padding: 0; margin: 0;} （不建议）  淘宝的样式初始化： body, h1, h2, h3, h4, h5, h6, hr, p, blockquote, dl, dt, dd, ul, ol, li, pre, form, fieldset, legend, button, input, textarea, th, td { margin:0; padding:0; }body, button, input, select, textarea { font:12px/1.5tahoma, arial, \5b8b\4f53; }h1, h2, h3, h4, h5, h6{ font-size:100%; }address, cite, dfn, em, var { font-style:normal; }code, kbd, pre, samp { font-family:couriernew, courier, monospace; }small{ font-size:12px; }ul, ol { list-style:none; }a { text-decoration:none; }a:hover { text-decoration:underline; }sup { vertical-align:text-top; }sub{ vertical-align:text-bottom; }legend { color:#000; }fieldset, img { border:0; }button, input, select, textarea { font-size:100%; }table { border-collapse:collapse; border-spacing:0; } 
absolute的containing block计算方式跟正常流有什么不同？
position跟display、margin collapse、overflow、float这些特性相互叠加后会怎么样？
对BFC规范的理解？
（W3C CSS 2.1 规范中的一个概念,它决定了元素如何对其内容进行定位,以及与其他元素的关 系和相互作用。）
css定义的权重
以下是权重的规则：标签的权重为1，class的权重为10，id的权重为100，以下例子是演示各种定义的权重值： /*权重为1*/div{}/*权重为10*/.class1{}/*权重为100*/#id1{}/*权重为100+1=101*/#id1 div{}/*权重为10+1=11*/.class1 div{}/*权重为10+10+1=21*/.class1 .class2 div{}   如果权重相同，则最后定义的样式会起作用，但是应该避免这种情况出现
解释下浮动和它的工作原理？清除浮动的技巧
用过媒体查询，针对移动端的布局吗？
使用 CSS 预处理器吗？喜欢那个？
SASS 
如果需要手动写动画，你认为最小时间间隔是多久，为什么？（阿里）
多数显示器默认频率是60Hz，即1秒刷新60次，所以理论上最小间隔为1/60＊1000ms ＝ 16.7ms
display:inline-block 什么时候会显示间隙？(携程)
移除空格、使用margin负值、使用font-size:0、letter-spacing、word-spacing
JavaScript
JavaScript原型，原型链 ? 有什么特点？
eval是做什么的？
它的功能是把对应的字符串解析成JS代码并运行； 应该避免使用eval，不安全，非常耗性能（2次，一次解析成js语句，一次执行）。
null，undefined 的区别？
写一个通用的事件侦听器函数。
    // event(事件)工具集，来源：github.com/markyun     markyun.Event = {         // 页面加载完成后         readyEvent : function(fn) {             if (fn==null) {                 fn=document;             }             var oldonload = window.onload;             if (typeof window.onload != 'function') {                 window.onload = fn;             } else {                 window.onload = function() {                     oldonload();                     fn();                 };             }         },         // 视能力分别使用dom0||dom2||IE方式 来绑定事件         // 参数： 操作的元素,事件名称 ,事件处理程序         addEvent : function(element, type, handler) {             if (element.addEventListener) {                 //事件类型、需要执行的函数、是否捕捉                 element.addEventListener(type, handler, false);             } else if (element.attachEvent) {                 element.attachEvent('on' + type, function() {                     handler.call(element);                 });             } else {                 element['on' + type] = handler;             }         },         // 移除事件         removeEvent : function(element, type, handler) {             if (element.removeEnentListener) {                 element.removeEnentListener(type, handler, false);             } else if (element.datachEvent) {                 element.detachEvent('on' + type, handler);             } else {                 element['on' + type] = null;             }         },          // 阻止事件 (主要是事件冒泡，因为IE不支持事件捕获)         stopPropagation : function(ev) {             if (ev.stopPropagation) {                 ev.stopPropagation();             } else {                 ev.cancelBubble = true;             }         },         // 取消事件的默认行为         preventDefault : function(event) {             if (event.preventDefault) {                 event.preventDefault();             } else {                 event.returnValue = false;             }         },         // 获取事件目标         getTarget : function(event) {             return event.target || event.srcElement;         },         // 获取event对象的引用，取到事件的所有信息，确保随时能使用event；         getEvent : function(e) {             var ev = e || window.event;             if (!ev) {                 var c = this.getEvent.caller;                 while (c) {                     ev = c.arguments[0];                     if (ev && Event == ev.constructor) {                         break;                     }                     c = c.caller;                 }             }             return ev;         }     }; 
Node.js的适用场景？
高并发、聊天、实时消息推送
介绍js的基本数据类型。
number,string,boolean,object,undefined
Javascript如何实现继承？
通过原型和构造器
["1", "2", "3"].map(parseInt) 答案是多少？
 [1, NaN, NaN] 因为 parseInt 需要两个参数 (val, radix) 但 map 传了 3 个 (element, index, array)
如何创建一个对象? （画出此对象的内存图）
  function Person(name, age) {     this.name = name;     this.age = age;     this.sing = function() { alert(this.name) }    } 
谈谈This对象的理解。
this是js的一个关键字，随着函数使用场合不同，this的值会发生变化。  但是有一个总原则，那就是this指的是调用函数的那个对象。 this一般情况下：是全局对象Global。 作为方法调用，那么this就是指这个对象 
事件是？IE与火狐的事件机制有什么区别？ 如何阻止冒泡？
 1. 我们在网页中的某个操作（有的操作对应多个事件）。例如：当我们点击一个按钮就会产生一个事件。是可以被 JavaScript 侦测到的行为。    2. 事件处理机制：IE是事件冒泡、火狐是 事件捕获；  3. ev.stopPropagation();
什么是闭包（closure），为什么要用它？
执行say667()后,say667()闭包内部变量会存在,而闭包内部函数的内部变量不会存在.使得Javascript的垃圾回收机制GC不会收回say667()所占用的资源，因为say667()的内部函数的执行需要依赖say667()中的变量。这是对闭包作用的非常直白的描述.    function say667() {     // Local variable that ends up within closure     var num = 666;     var sayAlert = function() { alert(num); }     num++;     return sayAlert; }   var sayAlert = say667();  sayAlert()//执行结果应该弹出的667  
"use strict";是什么意思 ? 使用它的好处和坏处分别是什么？
如何判断一个对象是否属于某个类？
  使用instanceof （待完善）     if(a instanceof Person){        alert('yes');    }
new操作符具体干了什么呢?
     1、创建一个空对象，并且 this 变量引用该对象，同时还继承了该函数的原型。      2、属性和方法被加入到 this 引用的对象中。      3、新创建的对象由 this 所引用，并且最后隐式的返回 this 。 var obj  = {}; obj.__proto__ = Base.prototype; Base.call(obj); 
Javascript中，有一个函数，执行时对象查找时，永远不会去查找原型，这个函数是？
hasOwnProperty
JSON 的了解？
JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式。 它是基于JavaScript的一个子集。数据格式简单, 易于读写, 占用带宽小 {'age':'12', 'name':'back'}
js延迟加载的方式有哪些？
defer和async、动态创建DOM方式（用得最多）、按需异步载入js
ajax 是什么?
同步和异步的区别?
如何解决跨域问题?
jsonp、 iframe、window.name、window.postMessage、服务器上设置代理页面
模块化怎么做？
立即执行函数,不暴露私有成员
    var module1 = (function(){     　　　　var _count = 0;     　　　　var m1 = function(){     　　　　　　//...     　　　　};     　　　　var m2 = function(){     　　　　　　//...     　　　　};     　　　　return {     　　　　　　m1 : m1,     　　　　　　m2 : m2     　　　　};     　　})(); 
AMD（Modules/Asynchronous-Definition）、CMD（Common Module Definition）规范区别？
异步加载的方式有哪些？
  (1) defer，只支持IE    (2) async：    (3) 创建script，插入到DOM中，加载完毕后callBack
documen.write和 innerHTML的区别
document.write只能重绘整个页面
innerHTML可以重绘页面的一部分
.call() 和 .apply() 的区别？
  例子中用 add 来替换 sub，add.call(sub,3,1) == add(3,1) ，所以运行结果为：alert(4);     注意：js 中的函数其实是对象，函数名是对 Function 对象的引用。      function add(a,b)     {         alert(a+b);     }      function sub(a,b)     {         alert(a-b);     }      add.call(sub,3,1);  
Jquery与jQuery UI 有啥区别？
*jQuery是一个js库，主要提供的功能是选择器，属性修改和事件绑定等等。  *jQuery UI则是在jQuery的基础上，利用jQuery的扩展性，设计的插件。  提供了一些常用的界面元素，诸如对话框、拖动行为、改变大小行为等等
JQuery的源码看过吗？能不能简单说一下它的实现原理？
jquery 中如何将数组转化为json字符串，然后再转化回来？
jQuery中没有提供这个功能，所以你需要先编写两个jQuery的扩展：
    $.fn.stringifyArray = function(array) {         return JSON.stringify(array)     }      $.fn.parseArray = function(array) {         return JSON.parse(array)     }       然后调用：     $("").stringifyArray(array)
针对 jQuery 的优化方法？
*基于Class的选择性的性能相对于Id选择器开销很大，因为需遍历所有DOM元素。  *频繁操作的DOM，先缓存起来再操作。用Jquery的链式调用更好。     比如：var str=$("a").attr("href");  *for (var i = size; i < arr.length; i++) {}  for 循环每一次循环都查找了数组 (arr) 的.length 属性，在开始循环的时候设置一个变量来存储这个数字，可以让循环跑得更快：   for (var i = size, length = arr.length; i < length; i++) {}
JavaScript中的作用域与变量声明提升？
如何编写高性能的Javascript？
那些操作会造成内存泄漏？
内存泄漏指任何对象在您不再拥有或需要它之后仍然存在。 垃圾回收器定期扫描对象，并计算引用了每个对象的其他对象的数量。如果一个对象的引用数量为 0（没有其他对象引用过该对象），或对该对象的惟一引用是循环的，那么该对象的内存即可回收。 setTimeout 的第一个参数使用字符串而非函数的话，会引发内存泄漏。 闭包、控制台日志、循环（在两个对象彼此引用且彼此保留时，就会产生一个循环）
JQuery一个对象可以同时绑定多个事件，这是如何实现的？
如何判断当前脚本运行在浏览器还是node环境中？（阿里）
通过判断Global对象是否为window，如果不为window，当前脚本没有运行在浏览器中
其他问题
你遇到过比较难的技术问题是？你是如何解决的？
常使用的库有哪些？常用的前端开发工具？开发过什么应用或组件？
页面重构怎么操作？
列举IE 与其他浏览器不一样的特性？
99%的网站都需要被重构是那本书上写的？
什么叫优雅降级和渐进增强？
WEB应用从服务器主动推送Data到客户端有那些方式？
对Node的优点和缺点提出了自己的看法？
*（优点）因为Node是基于事件驱动和无阻塞的，所以非常适合处理并发请求，   因此构建在Node上的代理服务器相比其他技术实现（如Ruby）的服务器表现要好得多。   此外，与Node代理服务器交互的客户端代码是由javascript语言编写的，   因此客户端和服务器端都用同一种语言编写，这是非常美妙的事情。  *（缺点）Node是一个相对新的开源项目，所以不太稳定，它总是一直在变，   而且缺少足够多的第三方库支持。看起来，就像是Ruby/Rails当年的样子。
你有哪些性能优化的方法？
 （看雅虎14条性能优化原则）。    （1） 减少http请求次数：CSS Sprites, JS、CSS源码压缩、图片大小控制合适；网页Gzip，CDN托管，data缓存 ，图片服务器。    （2） 前端模板 JS+数据，减少由于HTML标签导致的带宽浪费，前端用变量保存AJAX请求结果，每次操作本地变量，不用请求，减少请求次数    （3） 用innerHTML代替DOM操作，减少DOM操作次数，优化javascript性能。    （4） 当需要设置的样式很多时设置className而不是直接操作style。    （5） 少用全局变量、缓存DOM节点查找的结果。减少IO读取操作。    （6） 避免使用CSS Expression（css表达式)又称Dynamic properties(动态属性)。    （7） 图片预加载，将样式表放在顶部，将脚本放在底部  加上时间戳。    （8） 避免在页面的主体布局中使用table，table要等其中的内容完全下载之后才会显示出来，显示比div+css布局慢。
http状态码有那些？分别代表是什么意思？
100-199 用于指定客户端应相应的某些动作。  200-299 用于表示请求成功。  300-399 用于已经移动的文件并且常被包含在定位头信息中指定新的地址信息。  400-499 用于指出客户端的错误。400    1、语义有误，当前请求无法被服务器理解。401   当前请求需要用户验证 403  服务器已经理解请求，但是拒绝执行它。 500-599 用于支持服务器错误。 503 – 服务不可用
一个页面从输入 URL 到页面加载显示完成，这个过程中都发生了什么？（流程说的越详细越好）
    查找浏览器缓存      DNS解析、查找该域名对应的IP地址、重定向（301）、发出第二个GET请求     进行HTTP协议会话     客户端发送报头(请求报头)     服务器回馈报头(响应报头)     html文档开始下载     文档树建立，根据标记请求所需指定MIME类型的文件     文件显示     [     浏览器这边做的工作大致分为以下几步：      加载：根据请求的URL进行域名解析，向服务器发起请求，接收文件（HTML、JS、CSS、图象等）。      解析：对加载到的资源（HTML、JS、CSS等）进行语法解析，建议相应的内部数据结构（比如HTML的DOM树，JS的（对象）属性表，CSS的样式规则等等）     }
除了前端以外还了解什么其它技术么？你最最厉害的技能是什么？
你常用的开发工具是什么，为什么？
对前端界面工程师这个职位是怎么样理解的？它的前景会怎么样？
     前端是最贴近用户的程序员，比后端、数据库、产品经理、运营、安全都近。     1、实现界面交互     2、提升用户体验     3、有了Node.js，前端可以实现服务端的一些事情  前端是最贴近用户的程序员，前端的能力就是能让产品从 90分进化到 100 分，甚至更好，   参与项目，快速高质量完成实现效果图，精确到1px；   与团队成员，UI设计，产品经理的沟通；   做好的页面结构，页面重构和用户体验；   处理hack，兼容、写出优美的代码格式；   针对服务器的优化、拥抱最新前端技术。
加班的看法？
加班就像借钱，原则应当是------救急不救穷
平时如何管理你的项目？
        先期团队必须确定好全局样式（globe.css），编码模式(utf-8) 等；          编写习惯必须一致（例如都是采用继承式的写法，单样式都写成一行）；          标注样式编写人，各模块都及时标注（标注关键样式调用的地方）；          页面进行标注（例如 页面 模块 开始和结束）；          CSS跟HTML 分文件夹并行存放，命名都得统一（例如style.css）；          JS 分文件夹存放 命名以该JS功能为准的英文翻译。          图片采用整合的 images.png png8 格式文件使用 尽量整合在一起使用方便将来的管理
如何设计突发大规模并发架构？
说说最近最流行的一些东西吧？常去哪些网站？
    Node.js、Mongodb、npm、MVVM、MEAN、three.js 
移动端（Android IOS）怎么做好用户体验?
    清晰的视觉纵线、信息的分组、极致的减法、     利用选择代替输入、标签及文字的排布方式、     依靠明文确认密码、合理的键盘利用、
你在现在的团队处于什么样的角色，起到了什么明显的作用？
你认为怎样才是全端工程师（Full Stack developer）？
介绍一个你最得意的作品吧？
你的优点是什么？缺点是什么？
如何管理前端团队?
最近在学什么？能谈谈你未来3，5年给自己的规划吗？
想问公司的问题？
    问公司问题：     目前关注哪些最新的Web前端技术（未来的发展方向）？     前端团队如何工作的（实现一个产品的流程）？     公司的薪资结构是什么样子的？
居中浮动元素代码不对,
这是我从别人那里拿来的代码:
css的样式:
.bb1{width:500px;border:1px solid #333;padding:10px;margin:0 auto;}
.bb2{float:left;position:relative;left:50%;} /*核心代码*/
.bb2 a{position:relative;right:50%;}
<div class=\"bb1 clearfix\">
<div class=\"bb2\">
<a href=\"http://blog.163.com/l_lihanyu/blog/\">导航1</a>
<a href=\"http://blog.163.com/l_lihanyu/blog/\">导航2</a>
<a href=\"http://blog.163.com/l_lihanyu/blog/\">导航3</a>
<a href=\"http://blog.163.com/l_lihanyu/blog/\">导航4</a>
<a href=\"http://blog.163.com/l_lihanyu/blog/\">导航5</a>
</div>
</div>



百度错题
1、	请给Array本地对象增加一个原型方法，它用于删除数组条目中重复的条目(可能有多个)，返回值是一个包含被删除的重复条目的新数组。
答案：
1、Array.prototype.distinct = function() {
    var ret = [];
    for (var i = 0; i < this.length; i++) 
    {
        for (var j = i+1; j < this.length;) {    
            if (this[i] === this[j]) {
                ret.push(this.splice(j, 1)[0]);
            } else {
                j++;
            }
        }
     }
     return ret;
}
//for test
alert(['a','b','c','d','b','a','e'].distinct());
•	2、Array.prototype.distinct=function(){ 
var arr=[];
var obj={};
for(var i=0;i<this.length;i++){
if(obj[this[i]]==undefined)
obj[this[i]]=this[i];
else if(obj[this[i]])
arr.push(this[i]);
}
return arr;
}
alert(['a','b','c','d','b','a','e'].distinct());
3、Array.prototype.distinct = function (){
      var ret = [];
      for(var i=0;i<this.length;i++){
        if(this.indexOf(this[i])!=i){
            ret.push(this[i]);
        }
      }
      return ret;
  }
  alert(['a','b','c','d','b','"a"','e','1','2','3','2','"3"'].distinct()
2、请填充代码，使mySort()能使传入的参数按照从小到大的顺序显示出来。
function mySort() {
    var tags = new Array();//使用数组作为参数存储容器
    请补充你的代码
    return tags;//返回已经排序的数组
}
 
var result = mySort(50,11,16,32,24,99,57,100);/传入参数个数不确定
console.info(result);//显示结果
答案：
function mySort() {
    var tags = new Array();
    for(var i = 0;i < arguments.length;i++) {
        tags.push(arguments[i]);
    }
    tags.sort(function(compare1,compare2) {
        return compare1- compare2;
    });
    return tags;
}
 
var result = mySort(50,11,16,32,24,99,57,100);
console.info(result);
2、	flash和js通过什么类如何交互? ExternalInterface
3、请给出这段代码的运行结果（2 1 ） 
1
2
3
4
5
6
7
8
9	<SCRIPT LANGUAGE="JavaScript">
var bb = 1;
function aa(bb) {
    bb = 2;
    alert(bb);
};
aa(bb);
alert(bb);
</SCRIPT>
4、请用CSS实现如下图的样式，相关尺寸如图示，其中dom结构为：
<div id=”demo”></div>
 

答案：
#demo {
    width: 100px;
    height: 100px;
    background-color: #fff;
    position: relative;
    border: 2px solid #333;
}
 
#demo:after, #demo:before {
    border: solid transparent;
    content: ' ';
    height: 0;
    left: 100%;
    position: absolute;
    width: 0;
}
 
#demo:after {
    border-width: 10px;
    border-left-color: #fff;
    top: 20px;
}
 
#demo:before {
    border-width: 12px;
    border-left-color: #000;
    top: 18px;
}

3、	简述document.write和 innerHTML的区别。
document.write只能重绘整个页面,
innerHTML可以重绘页面的一部分。
•	document.write是直接写入到页面的内容流，如果在写之前没有调用document.open, 浏览器会自动调用open。每次写完关闭之后重新调用该函数，会导致页面被重写。 
innerHTML则是DOM页面元素的一个属性，代表该元素的html内容。你可以精确到某一个具体的元素来进行更改。如果想修改document的内容，则需要修改document.documentElement.innerElement。 

innerHTML很多情况下都优于document.write，其原因在于其允许更精确的控制要刷新页面的那一个部分。
4、	用户从手机的浏览器访问www.baidu.com，看到的可能跟桌面PC电脑，是不太一样的网页效果，会更适合移动设备使用。请简要分析一下，实现这种网页区分显示的原因及技术原理。
手机的网速问题、屏幕大小、内存、CPU等。通过不同设备的特征，实现不同的网页展现或输出效果。根据useragent、屏幕大小信息、IP、网速、css media Query等原理，实现前端或后端的特征识别和行为改变。
5、Flappy Bird是风靡一时的手机游戏，玩家要操作一只小鸟穿过无穷无尽的由钢管组成的障碍。如果要你在HTML前端开发这个游戏，为了保证游戏的流畅运行，并长时间运行也不会崩溃，请列举开发要注意的性能问题和解决的方法。
 
•	背景的卷轴效果优化。背景不能是无限长的图片拼接，必须有回收已移出的场景的方法。 
将复杂运算从主UI线程中解耦。比如场景中小鸟的运动轨迹、碰撞算法等，需要在空闲时间片运算，不能和UI动画同时进行。 
将比较大的运算分解成不同的时间片，防止阻塞主UI线程。最好使用webworker。 
注意内存泄漏和回收。使用对象池管理内存，提高内存检测和垃圾回收。 
进行预处理。将一些常用的过程进行预处理， 
控制好帧率。将1秒分解成多个时间片，在固定间隔时间片进行UI动画，其他时间片用在后台运算。 
通过 GPU  加速和 CSS transition  将小鸟飞行动画和背景动画分离
6、如下图，请实现表格信息的排序功能，当点击表头的属性区域，将表格信息进行排序切换功能，即第一次点击为降序排序，再一次点击进行升序排序。
 

答案：
1、<!DOCTYPE html>
 <html>
 <head>
     <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />

 <style>

 td{text-align:center;}

 </style>

 </head>
 <body>
 <table id="table" border="1px" width="350px;">
 <thead>
 <tr><td>姓名</td><td>力量</td><td>敏捷</td><td>智力</td></tr>
 </thead>
 <tbody>
 <tr><td>德鲁伊</td><td>17</td><td>24</td><td>13</td></tr>
 <tr><td>月之骑士</td><td>15</td><td>22</td><td>16</td></tr>
 <tr><td>众神之王</td><td>19</td><td>15</td><td>20</td></tr>
 <tr><td>流浪剑客</td><td>23</td><td>15</td><td>14</td></tr>
 </tbody>
 </table>
 <script>
 var oDiv=document.getElementById('table');
 var t=oDiv.tBodies[0].rows;
 var h=oDiv.getElementsByTagName('thead')[0].getElementsByTagName('td');
 var arr=[];
 function get(x,param)
 {
 for(var i=0;i<oDiv.tBodies[0].rows.length;i++)
 {
 arr[i]=oDiv.tBodies[0].rows[i];
 }

 arr.sort(function(tr1,tr2)
 {
 
 var n1=parseInt(tr1.cells[x].innerHTML);
 var n2=parseInt(tr2.cells[x].innerHTML);
 if(param==0)
 return n2-n1;
 else return n1-n2;
 })

 for(var i=0;i<arr.length;i++)
 {
 oDiv.appendChild(arr[i]);
 }
 }
 for(var i=1;i<h.length;i++)
 {
 var j=0;
 h[i].index=i;
 h[i].onclick=function()
 {
 j++;
 
 get(this.index,j%2);
 }
 }
 </script>
 </body>
 </html>
•	2、<!DOCTYPE html> 
<html lang="en"> 
<head> 
<meta charset="UTF-8"> 
<title>table_seq</title> 
<style type="text/css"> 
#div_wrapper{ 
width: 500px; 
height: 235px; 
position: absolute; 
left: 50%; 
top:50%; 
margin-left: -250px; 
margin-top: -200px; 
border: 1px solid silver; 
} 
#div_content table tr td{ 
width: 120px; 
border:1px solid silver; 
text-align: center; 
height: 40px; 
line-height: 40px; 
} 
#div_content table thead td{ 
background-color:silver; 
} 
#div_content table thead td:hover{ 
cursor: pointer; 
} 
</style> 
<script type="text/javascript"> 
// 如下图，请实现表格信息的排序功能，当点击表头的属性区域，将表格信息进行排序切换功能，即第一次点击为降序排序，再一次点击进行升序排序。 
var name,power,quick,smart,tbody,person;  
var clicked_p=false,clicked_s=false,clicked_q=false; 
person=[]; 
window.onload=function(){ 
name=document.getElementById('name'); 
power=document.getElementById("power"); 
quick=document.getElementById("quick"); 
smart=document.getElementById("smart"); 
tbody=document.getElementsByTagName("tbody"); 

var Nodes=tbody[0].getElementsByTagName("tr"); 
// 将数据保存到数组person中 
for (var i = 0; i < Nodes.length; i++) { 
var per=[]; 
var child=Nodes[i].childNodes; 
for (var j = 0; j < child.length; j++) { 
if(child[j].nodeName=="TD"){ 
per.push(child[j].innerHTML) 
} 
} 
person.push(per); 
} 
console.log(person); 
// 事件注册 
power.addEventListener("click",function(){ 
revertBypower(); 
}); 
quick.addEventListener("click",function(){ 
revertByquick(); 
}); 
smart.addEventListener("click",function(){ 
revertBysmart(); 
}); 
} 
function revertBypower(){ 
if(!clicked_p){ 
person.sort(function(value1,value2){return value1[1]>=value2[1]?1:-1}); 
clicked_p=true; 
} 
else{ 
person.sort(function(value1,value2){return value1[1]>=value2[1]?-1:1}); 
clicked_p=false; 
} 
refreshTable(); 
} 

function revertByquick(){ 
if(!clicked_q){ 
person.sort(function(value1,value2){return value1[2]>=value2[2]?1:-1}); 
clicked_q=true; 
} 
else{ 
person.sort(function(value1,value2){return value1[2]>=value2[2]?-1:1}); 
clicked_q=false; 
} 
refreshTable(); 
} 

function revertBysmart(){ 
if(!clicked_s){ 
person.sort(function(value1,value2){return value1[3]>=value2[3]?1:-1}); 
clicked_s=true; 
} 
else{ 
person.sort(function(value1,value2){return value1[3]>=value2[3]?-1:1}); 
clicked_s=false; 
} 
refreshTable(); 
} 

function refreshTable(){ 
for (var i = 0; i < person.length; i++) { 
for(var j=0;j<person[i].length;j++){ 
//alert(person[i][j]) 
document.getElementById("div"+i).childNodes[2*j+1].innerHTML=person[i][j]; 
} 
}; 
} 
</script> 
</head> 
<body> 
<div id="div_wrapper"> 
<div id="div_content"> 
<table> 
<thead> 
<tr> 
<td id="name">姓名</td> 
<td id="power">力量</td> 
<td id="quick">敏捷</td> 
<td id="smart">智力</td> 
</tr> 
</thead> 
<tbody> 
<tr id="div0"> 
<td>德鲁伊</td> 
<td>17</td> 
<td>24</td> 
<td>13</td> 
</tr> 
<tr id="div1"> 
<td>月之骑士</td> 
<td>15</td> 
<td>22</td> 
<td>16</td> 
</tr> 
<tr id="div2"> 
<td>众神之王</td> 
<td>19</td> 
<td>15</td> 
<td>20</td> 
</tr> 
<tr id="div3"> 
<td>流浪剑客</td> 
<td>23</td> 
<td>15</td> 
<td>14</td> 
</tr> 
</tbody> 
</table> 
</div> 
</div> 
</body> 
</html> 
3、/** 满足以下需求：
* 1.点击姓名所在列的th，不会排序
* 2.第一次点击一个th，默认排序为降序；
* 3.连续点击同一个th，排序方式会变换；
*/
 
//获取点击的th所在列的td的数据
var getColTdsData = function(target) {
 
    var index = $(target).index(),
        $rows = $(target).parents("table").children('tbody').children('tr'),
        colTdsData = [],
        i,
        len,
        tdInRow;
 
    //点击姓名列
    if (index === 0) {
        return null;
    }
     
    for (i = 0, len = $rows.length; i < len; i++) {
         
            tdInRow = $($rows)[i].childNodes;
            colTdsData.push(tdInRow[index].innerHTML);
    }
 
    return colTdsData;
};
 
 
//降序
var sortDescend = function(array) {
 
    var sortIndex = [],
        i,
        len = array.length,
        j,
        temp;
 
    //初始化sortIndex    
    for (i = 0; i < len; i++) {
        sortIndex[i] = i;
    }
 
    //array排序，sortIndex相应位置互换
    for (i = 0; i < len; i++) {
 
        for (j = i+1; j < len; j++) {
 
            if (array[i] < array[j]) {
                 
                //先对array进行排序
                temp = array[i];
                array[i] = array[j];
                array[j] = temp;
 
                //再对sortIndex进行位置互换
                temp = sortIndex[i];
                sortIndex[i] = sortIndex[j];
                sortIndex[j] = temp
            }
        }
    }
 
    return sortIndex;
};
 
 
//升序
var sortAscend = function(array) {
 
    var sortIndex = [],
        i,
        len = array.length,
        j,
        temp;
 
    //初始化sortIndex    
    for (i = 0; i < len; i++) {
        sortIndex[i] = i;
    }
 
    //array排序，sortIndex相应位置互换
    for (i = 0; i < len; i++) {
 
        for (j = i+1; j < len; j++) {
 
            if (array[i] > array[j]) {
                 
                //先对array进行排序
                temp = array[i];
                array[i] = array[j];
                array[j] = temp;
 
                //再对sortIndex进行位置互换
                temp = sortIndex[i];
                sortIndex[i] = sortIndex[j];
                sortIndex[j] = temp;
            }
        }
    }
 
    return sortIndex;
};
 
//根据排好的行号重写tbody
var changeTabelRow = function(target,sortedRowIndex) {
 
    var $tbody = $(target).parents("table").children('tbody'),
        $rows = $tbody.children("tr"),
        i,
        len,
        str = "";
 
    for (i = 0, len = sortedRowIndex.length; i < len; i++) {
        str += "<tr>" + $rows.eq(sortedRowIndex[i]).html() + "</tr>";
    }
 
    $tbody.html(str);
};
 
//使用闭包，避免使用全局变量
var handler = function() {
     
    var previousTarget = null,
        count = 0; //记录重复点击的次数
 
    return function(event) {
        var target = event.target,
            colTdsValues,
            sortedIndex;
 
        //获取列元素数据
        colTdsValues = getColTdsData(target);
 
        //点击姓名列
        if (colTdsValues === null) {
            return;
        }    
 
        //第一次点击
        if (previousTarget !== target) {
            sortedIndex = sortDescend(colTdsValues);
            count = 0;
        }
 
        //相邻两次target相同
        if (previousTarget === target) {
             
            count++;
 
            if (count%2 === 1) {
                sortedIndex = sortAscend(colTdsValues);
            }else{
                sortedIndex = sortDescend(colTdsValues);
            }
        }
 
        //换行
        changeTabelRow(target,sortedIndex);
 
        //记录本次target，以和下次target比较
        previousTarget = target;
    };
};
 
$("thead th").click(handler());
5、	你知道的，javascript语言的执行环境是"单线程模式"，这种模式的好处是实现起来比较简单，执行环境相对单纯；坏处是只要有一个任务耗时很长，后面的任务都必须排队等着，会拖延整个程序的执行，因此很多时候需要进行“异步模式”，请列举js异步编程的方法。
答案：回调函数，这是异步编程最基本的方法。
事件监听，另一种思路是采用事件驱动模式。任务的执行不取决于代码的顺序，而取决于某个事件是否发生。
发布/订阅，上一节的"事件"，完全可以理解成"信号"。
Promises对象，Promises 对象是CommonJS 工作组提出的一种规范，目的是为异步编程提供统一接口。
6、	用户从手机的浏览器访问www.baidu.com，看到的可能跟桌面PC电脑，是不太一样的网页效果，会更适合移动设备使用。请简要分析一下，实现这种网页区分显示的原因及技术原理。
答案：手机的网速问题、屏幕大小、内存、CPU等。通过不同设备的特征，实现不同的网页展现或输出效果。根据useragent、屏幕大小信息、IP、网速、css media Query等原理，实现前端或后端的特征识别和行为改变。

1、	判断是否为NaN
isNaN(a[i])&& typeof a[i]=="number"
2、	字符串邮箱
/^[a-z0-9_+.-]+\@([a-z0-9-]+\.)+[a-z0-9]{2,4}$/
阿里实习生笔试
1、指令集架构属于复杂指令集架构的是（CISC）
简单指令：ARM 、MIPS 、SPARC 
3、	IP数据报头采用（）字节序，在此字节序下从低地址到高地址0x1234的表示形式为 （big_endian,0 0 0x12 0x34） 。
解析：big_endian：高位在低地址； 
small-endian：地位在低地址。 
4、	设集合A={1,2,3},A上的关系R＝{(1,1),(2,2),(2,3),(3,2),(3,3)}，则R不具备 (反对称性)?
解析：假设集合A，以及基于A上的关系R 
自反： 如果a是A的元素，那么<a,a>是R的元素 
反自反： 如果a是A的元素，那么<a,a>不是R的元素 
对称：如果<a,b>是R的元素，那么<b,a>是R的元素 
反对称：如果<a,b>，<b,a>是R的元素，那么a,b相等 
传递：如果<a,b>，<b,c>是R的元素，那么<a,c>是R的元素 
                       2011阿里面试
1、请说明下面各种情况的执行结果，并注明产生对应结果的理由。 
1
2
3	function doSomething() { 
    alert(this); 
} 
① element.onclick = doSomething，点击element元素后。 
② element.onclick = function() {doSomething()}， 点击element元素后。 
③ 直接执行doSomething()。 
答案：①弹出element object，通过函数赋值方式，this直接指向element对象 
②弹出window object，this是写在doSomething这个函数里面的，而这种方式的事件绑定写法并没有将element对象传递给this，而在默认情况下this指向window 
③弹出window object，没有绑定对象的情况下this默认指向window 
2、阅读以下JavaScript代码： 
1
2
3
4
5
6
7
8
9
10
11	if (window.addEventListener) {
       var addListener = function(el, type, listener, useCapture) {
           el.addEventListener(type, listener, useCapture);
       };
   } else if (document.all) {
       addListener = function(el, type, listener) {
           el.attachEvent("on" + type, function() {
               listener.apply(el);
           });
       };
   }

请阐述 a) 代码的功能; b) 代码的优点和缺点; c) listener.apply(el) 在此处的作用; d) 如果有可改进之处，请给出改进后的代码，并说明理由。
答案：a) 功能：事件注册 
b) 优点：跨浏览器，特性探测，性能优化。缺点：document.all 
c) 作用：使得IE中listener的this 为 el，与其它浏览器一致 
d) 改进：document.all改成window.attachEvent; useCapture的默认 
3、请编写一个JavaScript 函数toRGB，它的作用是转换CSS中常用的颜色编码。 要求： 
1
2
3	alert(toRGB("#0000FF"));          // 输出 rgb(0, 0, 255)
alert(toRGB("invalid"));          // 输出 invalid 
alert(toRGB("#G00"));              // 输出 #G00
答案：自己的
（1）、function toRGB(color){
  var r=/^#([0-9a-fA-F]{2}){3}/;
if(r.test(color)){
if(color.length==7){
return "rgb("+parseInt(color.substr(1,2),16)+","+parseInt(color.substr(3,2),16)+","+parseInt(color.substr(5,2),16)+")";
}
if(color.length==4){
color=color.split("");
return "rgb("+parseInt(color[1],16)+","+parseInt(color[2],16)+","+parseInt(color[3],16)+")";
}
}
else return color;
} 
alert(toRGB("#0000FF"));  
（2）、function toRGB(color) {
    var regex = /^#([0-9a-fA-F]{2})([0-9a-fA-F]{2})([0-9a-fA-F]{2})$/
    match = color.match(regex)
    return match ? 'rgb('+parseInt(match[1], 16)+','+parseInt(match[2], 16)+','+parseInt(match[3], 16)+')' : color
}
4、var Obj = function(msg){
    this.msg = msg;
    this.shout = function(){
        alert(this.msg);
    }   
    this.waitAndShout = function(){
        //隔五秒钟后执行上面的shout方法
    }
答案：var Obj = function(msg){
    this.msg = msg;
    this.shout = function(){
        alert(this.msg);
    }    
    this.waitAndShout = function(){
        var that = this;
        setTimeout(that.shout, 5000);
        //隔五秒钟后执行上面的shout方法
    }
    return this;
}
Obj("shouting").waitAndShout();
5、请编写一个JavaScript函数，它的作用是校验输入的字符串是否是一个有效的电子邮件地址。要求： a)   使用正则表达式。 b)   如果有效返回true ，反之为false。
答案：var checkEmail  = function(email){
var preg ="(^[a-zA-Z]|^[\\w-_\\.]*[a-zA-Z0-9])@(\\w+\\.)+\\w+$";
    pregObj  =new RegExp(preg); 
    return pregObj.test(email);
}
5、	请用CSS定义p标签，要求实现以下效果: 字体颜色在IE6下为黑色(#000000)；IE7下为红色(#ff0000)；而其他浏览器下为绿色(#00ff00)。
答案：p{ 
    color:#0f0; 
    _color:#000; /*ie6*/    
} 
/*ie7*/ 
*+html p{ 
    color:#f00;
} 
或p{ color:#0f0; *color:#f00; _color:#000; }
6、请给JavaScript的String 原生对象添加一个名为trim 的原型方法，用于截取空白字符。要求 
1
2	alert(" taobao".trim());     // 输出 "taobao"
alert(" taobao ".trim());    // 输出 "taobao"
答案：String.prototype.trim = function() {          
    return this.replace(/^\s+|\s+$/g, "");     
};
7、请编写一个JavaScript函数 parseQueryString，它的用途是把URL参数解析为一个对象，如： 
1
2
3	var url = “http://www.taobao.com/index.php?key0=0&key1=1&key2=2.....”
var obj = parseQueryString(url);
alert(obj.key0)  // 输出0
答案：function parseQueryString ( name ){
  name = name.replace(/[\[]/,"\\\[").replace(/[\]]/,"\\\]");
  var regexS = "[\\?&]"+name+"=([^&#]*)";
  var regex = new RegExp( regexS );
  var results = regex.exec( window.location.href );
  if( results == null )
    return "";
  else
    return results[1];
}
7、	seesion和cookies的区别
如果不设置过期时间，则表示这个cookie生命周期为浏览器会话期间，只要关闭浏览器窗口，cookie就消失了。
2.session机制是一种服务器端的机制，服务器使用一种类似于散列表的结构(也可能就是使用散列表)来保存信息。但程序需要为某个客户端的请求创建一个session的时候，服务器首先检查这个客户端的请求里是否包含了一个session标识－称为session id,如果已经包含一个session id则说明以前已经为此客户创建过session，服务器就按照session id把这个session检索出来使用(如果检索不到，可能会新建一个，这种情况可能出现在服务端已经删除了该用户对应的session对象，但用户人为地在请求的URL后面附加上一个JSESSION的参数)。 
3.恰恰是由于关闭浏览器不会导致session被删除，迫使服务器为seesion设置了一个失效时间，当距离客户端上一次使用session的时间超过这个失效时间时，服务器就可以认为客户端已经停止了活动，才会把session删除以节省存储空间。
网易2015校招-前端工程师（笔试题） 
选择题 1.对于多关键字而言，那种文件组织方便而又高效(B)
A、顺序文件 B、倒排文件 C、散列文件 D、B+树索引文件

2.以下哪些算法可用于遍历网络图(AB)
A、广度优先搜索 B、深度优先搜索 C、线性规划策略 D、决策树

3.我们使用一个6元组来表示6个节点的无向图的顶点数，请问以下哪些6元组是可能的组合(BD)
A、<1,2,3,4,5,6> B、<2,4,4,2,3,5> C、<1,3,4,2,2,1> D、<1,2,2,4,5,2>
解析：题中的顶点数估计是度数，无向图<V,E>,e为边数，0<=e<=n(n-1)/2,且总度数=2e.
而AC中的总度数为1+2+3+4+5+6=21,1+3+4+2+2+1=13为奇数，故排除。n=6,故e<=15.

4.以下关于可计算性的说法正确的是()
A、所有问题最终都可以抽象为一个计算模型，图灵机可以在一个有限的时间(虽然可能会占用非常久的时间)内完成计算：现代计算机的设计正是基于该理论。
B、存在部分问题，我们无法在有限时间内，给出解答：但是，所有问题都可以在有限时间内验证其解答的正确性。
C、 Godel(哥德尔)第一定律指明不存在完备且相容的公理系统。
D、以上说法都不正确。

5. 16进制数值C396和8进制数值64474的异或结果值(10进制)为(A)
A、43690 B、16660 C、60350 D、20375

6.以下经典的问题哪些属于NP问题()
A、图灵停机问题 B、排序 C、0，1背包问题 D、枚举有限集合的所有子集
答：P问题可以找到在多项式时间内解决它的算法的问题。
NP问题可以在多项式时间内验证一个解的问题。
D可验证一个集合是否是有限集合的子集
B，C， D为正确。

7.存在以下字母串：AGDCCDDDGFBBFFGGDDDGGGEFFDDCCCDDDFGAAA现在需要对该串进行Huffman编码，那么字母F对应bit值(二进制格式为)(D)
A、10 B、11 C、110 D、101

8.进程管理如果设计不当将会导致“死锁”的产生，对待死锁，典型的银行家算法属于(1)，而剥夺资源属于(2)的方法。B
A、(1)=死锁预防，(2)=死锁避免
B、(1)=死锁预防，(2)=死锁解除
C、(1)=死锁避免，(2)=死锁预防
D、(1)=死锁避免，(2)=死锁解除

9.关于数据库索引，以下说法正确的是(D)
A、针对某些字段建立索引，能够有小减少相关数据库表的磁盘空间占用;
B、针对某些字段建立索引，能够有效的提升相关字段的读与写的效率;
C、常见数据库管理系统，通常使用hash表来存储索引;
D、数据库索引的存在，可能导致相关字段删除的效率降低; 
答：索引是一种提高数据库查询速度的机制，是与表或视图关联的磁盘上结构，即对表中列值排序的一种结构。
A.索引需要额外的磁盘空间，为一索引页，包含着索引记录，每条索引记录包含键值和逻辑指针。
B. 不会提升写效率
C.B+树
D.正确，删除相关字段需要动态维护索引，故效率降低。

简答题: 1、什么是闭包，闭包有什么用?请举例说明。
解析：Javascript中，函数内部可以读取全局变量，函数外部无法读取函数内部的局部变量。
function f1(){
    var n=1024;
    function f2(){
        console.log(n)
    }
    return f2();
}   
var foo =f1();
foo();
//以上函数f2()就是闭包

　　闭包就是能够读取其他函数内部变量的函数。


2.apply 和 call 的用法和区别。

3.bind 函数的兼容性
bind方法会创建一个新函数,称为绑定函数.当调用这个绑定函数时,绑定函数会以创建它时传入bind方法的第一个参数作为this,传入bind方法的第二个以及以后的参数加上绑定函数运行时本身的参数按照顺序作为原函数的参数来调用原函数.
4.参考给出的原型图和要求，手写 html，css和 js。
　　fun.bind(thisArg[, arg1[, arg2[, ...]]])
script type="text/javascript">  
     window.onload = function()  
     { 
	  
	 var nav=document.getElementById("nav");
	nav.onclick=function(e){
	var target=e.target;
	var contentId=target.getAttribute("href").slice(1);
	var m=document.getElementsByName("content");
	for(var i=0;i<m.length;i++){
	m[i].setAttribute("class","hide");
	}
	
	document.getElementById(contentId).removeAttribute("class");
	}
	 
    }  
      
    </script>  

5.飞机起飞时，人会感觉到有一股力压在身上，为什么?施力者是谁?

6.飞机平稳飞行后，你在过道跳起来，会不会撞到飞机尾部?

7.n是一个奇数，求证n(n^2-1)能被24整除
当n=1时，(n-1)n(n+1)=0,成立；
假设存在奇数k,使得(k-1)k(k+1)能被24整除；
证明n=k+2时，(k+1)(k+2)(k+3)能被24整除；
(k+1)(k+2)(k+3)=(k+1)(k-1)(k+3)+3(k+1)(k+3)
=(k+1)(k-1)k+3(k+1)(k-1)+3(k+1)*4
=(k+1)(k-1)k+6(k+1)(k-1)+(k+1)*12
(k+1)(k-1)k能被24整除
由于k是奇数，k+1和k-1都是偶数，所以6(k+1)(k-1),(k+1)*12都能被24整除
8.两个r进制的数，N和N',它们的位数相同，数字也都相同，只是排序不一样(比如12345和25413)求证N-N'能被r-1整除。

9.关于session的。 为什么使用session?使用session的根本原因是?假如你使用的编程语言没有提供对session的支持，请你使用伪代码实现session机制。 请说明在你实现的机制中的安全因素。
为什么使用session

原因：因为Http协议是短连接的，即一次性单向的 请求响应模式

服务器不能主动访问客户端，必须客户端进行请求服务端进行响应，但是服务器不能保存客户端的信息
因此web服务器引入了session，主要是保存客户端的信息。

【分析】1 为什么使用session？使用session的根本原因是？ 
session是为了维持客户端和服务器的会话，实际上就是通过这个机制，来判断当前访问的用户，是上次的那一个？也就是身份的辨认。 
2 session的机制和实现 
session一般通过cookie或者URL里的一个参数来实现。 
第一次访问，产生一个唯一的session编号，然后发送给客户端，比如传递cookie,或者在url里面加上额外的参数 
服务器在一个Map里保存此编号对应的信息 
用户下一次访问，会再次传递这个编号，服务器在map里查找对应编号的信息是否存在，并进行后面的操作
最关键的，就是sessionid 的生成算法，要足够的随机性，且长度足够长。 除非不得已，不要放在url里面传递 
4 多个机器 
这个是集群的基础，session至少要在另一个机器上保持同步，也就是这个机器的某个session的任何改变，都要在另一个机器上同时改变。 当然，如果所有机器都改变也行，不过网络流量大了一些毕竟2个机器同时出故障的几率已经很低了。 
同步的机制可以用消息的方法进行，比如JMS/UDP等。如果同步有问题，则必须尝试，除非系统只剩下最后一台机器了。 
5 故障恢复 
因为有至少一个session的备份，所以故障后应立即让备份的机器接管，并继续服务，同时让另外一个机器再次作为备份。 
系统如果有管理机，则可以实现简单的故障切换，否则只能每个session进行整个集群的备份了，这样任何一个机器接管都没有问题了。
10.假如要让你的机制实现多个web服务器前端(几多个机器)，你要怎样实现?假如要让你的机制实现勿单点故障点(即一台机器当掉，不影响整个系统的运行)，你要怎样实现?


