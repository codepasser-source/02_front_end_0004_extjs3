 Ext 3.0  学习笔记

<<<<<<<<<<<<<<<<<<<<第一章 应用ExtJS<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<< 
 -Ext 配置  cope Ext-3.0 lib 下的文件放在webroot下

 
 <link rel="stylesheet" type="text/css" href="../ext/resources/css/ext-all.css" />
 <script type="text/javascript" src="../ext/adapter/ext/ext-base.js"></script>
 <script type="text/javascript" src="../ext/ext-all.js"></script>
 <script type="text/javascript" src="../ext/ext-lang-zh_CN.js"></script>


 adapter：负责将里面提供第三方底层库（包括Ext 自带的底层库）映射为Ext 所支持
的底层库。
build： 压缩后的ext 全部源码(里面分类存放)。
docs： API 帮助文档。
exmaples：提供使用ExtJs 技术做出的小实例。
resources：Ext UI 资源文件目录，如CSS、图片文件都存放在这里面。
source： 无压缩Ext 全部的源码(里面分类存放) 遵从Lesser GNU （LGPL） 开源的
协议。
ExtJS 实用简明教程[收集整理:龚辟愚、QQ 群：19274175]
- 5 -
Ext-all.js：压缩后的Ext 全部源码。
ext-all-debug.js：无压缩的Ext 全部的源码(用于调试)。
ext-core.js：压缩后的Ext 的核心组件，包括sources/core 下的所有类。
ext-core-debug.js：无压缩Ext 的核心组件，包括sources/core 下的所有类。

>>>>>>>>>>>>>>>>>>>>>第二章、开始ExtJS>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

2.1 -ExtJS版的helloworld   例程：Ext_1000_Base


注：在ExtJS 库文件及页面内容加载完后，ExtJS 会执行Ext.onReady 中指定的函数，因此
可以用，一般情况下每一个用户的ExtJS 应用都是从Ext.onReady 开始的
   
    a-弹出警示框  
      Ext.onReady( function() {
		Ext.MessageBox.alert("hello","hello,easyjf open source");      // 参数说明：（标题，显示文本）
	}); 

     b-打开一个新页面
       Ext.onReady( function() {                                                                 //匿名类
		var win = new Ext.Window(                                                    //Ext 中 Window对象
		  {title:"love",										// win设置属性  注意逗号
		   width:521,
		   height:521,
		   html:'<h2>DO YOU LOVE ME?</h2>'
		   }
		);
		
		win.show();									      //让窗口显示
	});


>>>>>>>>>>>>>>>>>>>>>第三章 Ext框架基础及核心简介>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>


3.1  Panel组件的使用 


      // 第一种方法
		var obj ={
		title:"div1",
		width:521,
		height:60,
	 
		html:'mine  1'		
		}; 
		var panel1 = new  Ext.Panel(obj);
		panel1.render("div1");                                       //显示区域 DIV  id
	//第二种方法
		var panel2 = new  Ext.Panel({
		title:"div2",
		width:521,
		height:60,
		 
		html:'mine  2'		
		});
		panel2.render("div2");
		
    //第三种方法
	  new  Ext.Panel({
		renderTo:'div3',                                                   //render属性
		title:"div3",
		width:521,
		height:60,		 
		html:'mine  3'		
		}); 
	});

3.2  TabPanel组件的使用
   
    var panel1=new Ext.TabPanel({
	    width:300,
		height:200,
		items:[
			new Ext.Panel( {
			      title:"面板1",
				  height:30,
				  html:'I love you xr,wait... I sure you is mine 1'
					  }),
			new Ext.Panel({
					  title:"面板2",
					  height:30,
						  html:'I love you xr,wait... I sure you is mine 2'
					  }),
			new Ext.Panel({
					  title:"面板3",
					  height:30,
						  html:'I love you xr,wait... I sure you is mine 3'
		              })
		]
	  });
        panel1.render("div1");                         //显示区域的 DIV


3.3  组件的配置属性


       参考 ext /docs/index.html


3.5  Extjs 组件的事件处理

ExtJS 提供了一套强大的事件处理机制，通过这些事件处理机制来响应用户的动作、监
控控件状态变化、更新控件视图信息、与服务器进行交互等等。事件统一由
Ext.EventManager 对象管理，与浏览器W3C 标准事件对象Event 相对应，Ext 封装了一个
Ext.EventObject 事件对象。支持事件处理的类(或接口)为Ext.util.Observable，凡是继承该类
的组件或类都支持往对象中添加事件处理及响应功能。



HTML机制 

<script>
function a()
{
alert('some thing');
}
window.onload=function(){
document.getElementById("btnAlert").onclick=a;                  //标准HTML文档 事件处理 文档被加载时 为 input设定 事件函数
}
</script>
<input id="btnAlert" type="button" value="alert框" />


Ext 事件处理类似机制
----------------------------click事件---------------------------------------------------------
<script  type="text/javascript">
 
   function a(){ 
     Ext.Msg.alert("love","i sure you is mine");
   }

  Ext.onReady( function() {      
	 Ext.get("btnAlert").addListener("click",a);                      // 获取元素设置 事件  (addListener  缩写 on)
         Ext.get("btndelay").on("click",a,this,{delay:2000});         //延迟时间执行
	});
	<input  id="btnAlert" type="button" value="onclick事件"/>
	<input  id="btndelay" type="button" value="delay 延迟"/>
</script> 

----------------------------beforedestroy 销毁前事件---------------------------------------------------------
function show(){ 
	 var win =  new Ext.Window( {
	  title:"win",
      width:500,
	  height:300,
      html:'关闭我是不可能的！！！.......'
	  });   
	  win.addListener("beforedestroy",function (obj){ 
	      obj.show();
		    Ext.Msg.alert("(*^__^*)","关不了吧？哈哈哈.... ");
	       return false; 
	  });
	  win.show();
   }

----------------------------------------------------------------------------------------------------------------

>>>>>>>>>>>>>>>>>>>>>第四章、使用面板>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
 
4.1 Panel    (0400)
     面板由以下几个部分组成，一个顶部工具栏、一个底部工具栏、面板头部、面板尾部、
面板主区域几个部分组件。面板类中还内置了面板展开、关闭等功能，并提供一系列可重
用的工具按钮使得我们可以轻松实现自定义的行为，面板可以放入其它任何容器中，面板本
身是一个容器，他里面又可以包含各种其它组件。
	new Ext.Panel({
		renderTo:"div1",
	    title:"面板header",
		width:400,
	    height:300,
       
		html:'面板主区域',
		tbar:[
			{text:'top1',height:60},
			{text:'top2'}
		],
		bbar:[
	           {text:'buttom1'},
                     {text:'buttom2'}
		],
        buttons:[
			{text:'button1'},
			{text:'button2'}		
		]
		});
//面板顶部工具栏（header--tools）
		new Ext.Panel({
		renderTo:"div2",
	         title:"面板header",
		width:400,
	          height:300, 
		html:"<h1>Hello,easyjf open source!</h1>",
		tools:[
			{id:"help",handler:function(){Ext.Msg.alert("help","please help me !")}},
			{id:"save"},
			{id:"close"}
		],
                   tbar:[{pressed:true,text:"刷新"}]
		});

//面板工具栏使用方法(tbar--Toolbar)
        new Ext.Panel({
		renderTo:"div3",
	         title:"面板header",
		width:400,
	         height:300, 
		html:"<h1>Hello,easyjf open source!</h1>",
	          tbar:[
		new Ext.Toolbar.TextItem("工具栏:"),
                    {xtype:"tbfill"},             //空白
                    {pressed:true,text:'添加'},
                    {xtype:"tbseparator"} ,  //分隔符
                    {pressed:true,text:'保存'} , 
		 {xtype:"tbbutton"},
                    {pressed:true,text:'按钮'} 
                    ]
   }); 
----------------------------------------------------------------------------------------------------------
4.2 选项的tabpanel  (0500)
Viewport 不需要再指定renderTo，而我们也看到Viewport 确实填充了整个浏览器显示区
域，并会随着浏览器显示区域大小的改变而改改,Viewport 主要用于应用程序的主界面，
可以通过使用不同的布局来搭建出不同风格的应用程序主界面。在Viewport 上常用的布局
有fit、border 等，当然在需要的时候其它布局也会常用。看下面的代码：


//普通布局
Ext.onReady(function(){
    new Ext.Viewport({
        enableTabScroll:true,
        layout:"fit",
        items:[{title:"面板",
        html:"",
        bbar:[
	   {text:"按钮1"},
            {text:"按钮2"}]
       }]
    });
});

//创建一个带菜单区域的面板布局
Ext.onReady(function(){
       new Ext.Viewport({
             enableTabScroll:true,
              layout:"border",
              items:[
	                  {region:"north",height:50,html:"<h1>网站后台管理系统!</h1>"},
				      {title:"menu",region:"west",width:200,collapsible:true,html:"<h1>菜单栏</h1>"},    // collapsible属性 可以收缩菜单
		                      {xtype:"tabpanel",region:"center",
				             items:[
				                 {title:"tabpanel1"} ,
						 {title:"tabpanel2"}
			                 ]
		   }                     
               ]
      });
});

>>>>>>>>>>>>>>>>>>>>>第五章、窗口及对话框>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
 
5.1、窗口基本应用
ExtJS 中窗口是由Ext.Window 类定义，该类继承自Panel，因此窗口其实是一种特殊的
面板Panel。窗口包含了浮动、可拖动、可关闭、最大化、最小化等特性。看下面的代码：











