 Ext 3.0  ѧϰ�ʼ�

<<<<<<<<<<<<<<<<<<<<��һ�� Ӧ��ExtJS<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<< 
 -Ext ����  cope Ext-3.0 lib �µ��ļ�����webroot��

 
 <link rel="stylesheet" type="text/css" href="../ext/resources/css/ext-all.css" />
 <script type="text/javascript" src="../ext/adapter/ext/ext-base.js"></script>
 <script type="text/javascript" src="../ext/ext-all.js"></script>
 <script type="text/javascript" src="../ext/ext-lang-zh_CN.js"></script>


 adapter�����������ṩ�������ײ�⣨����Ext �Դ��ĵײ�⣩ӳ��ΪExt ��֧��
�ĵײ�⡣
build�� ѹ�����ext ȫ��Դ��(���������)��
docs�� API �����ĵ���
exmaples���ṩʹ��ExtJs ����������Сʵ����
resources��Ext UI ��Դ�ļ�Ŀ¼����CSS��ͼƬ�ļ�������������档
source�� ��ѹ��Ext ȫ����Դ��(���������) ���Lesser GNU ��LGPL�� ��Դ��
Э�顣
ExtJS ʵ�ü����̳�[�ռ�����:�����ޡ�QQ Ⱥ��19274175]
- 5 -
Ext-all.js��ѹ�����Ext ȫ��Դ�롣
ext-all-debug.js����ѹ����Ext ȫ����Դ��(���ڵ���)��
ext-core.js��ѹ�����Ext �ĺ������������sources/core �µ������ࡣ
ext-core-debug.js����ѹ��Ext �ĺ������������sources/core �µ������ࡣ

>>>>>>>>>>>>>>>>>>>>>�ڶ��¡���ʼExtJS>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

2.1 -ExtJS���helloworld   ���̣�Ext_1000_Base


ע����ExtJS ���ļ���ҳ�����ݼ������ExtJS ��ִ��Ext.onReady ��ָ���ĺ��������
�����ã�һ�������ÿһ���û���ExtJS Ӧ�ö��Ǵ�Ext.onReady ��ʼ��
   
    a-������ʾ��  
      Ext.onReady( function() {
		Ext.MessageBox.alert("hello","hello,easyjf open source");      // ����˵���������⣬��ʾ�ı���
	}); 

     b-��һ����ҳ��
       Ext.onReady( function() {                                                                 //������
		var win = new Ext.Window(                                                    //Ext �� Window����
		  {title:"love",										// win��������  ע�ⶺ��
		   width:521,
		   height:521,
		   html:'<h2>DO YOU LOVE ME?</h2>'
		   }
		);
		
		win.show();									      //�ô�����ʾ
	});


>>>>>>>>>>>>>>>>>>>>>������ Ext��ܻ��������ļ��>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>


3.1  Panel�����ʹ�� 


      // ��һ�ַ���
		var obj ={
		title:"div1",
		width:521,
		height:60,
	 
		html:'mine  1'		
		}; 
		var panel1 = new  Ext.Panel(obj);
		panel1.render("div1");                                       //��ʾ���� DIV  id
	//�ڶ��ַ���
		var panel2 = new  Ext.Panel({
		title:"div2",
		width:521,
		height:60,
		 
		html:'mine  2'		
		});
		panel2.render("div2");
		
    //�����ַ���
	  new  Ext.Panel({
		renderTo:'div3',                                                   //render����
		title:"div3",
		width:521,
		height:60,		 
		html:'mine  3'		
		}); 
	});

3.2  TabPanel�����ʹ��
   
    var panel1=new Ext.TabPanel({
	    width:300,
		height:200,
		items:[
			new Ext.Panel( {
			      title:"���1",
				  height:30,
				  html:'I love you xr,wait... I sure you is mine 1'
					  }),
			new Ext.Panel({
					  title:"���2",
					  height:30,
						  html:'I love you xr,wait... I sure you is mine 2'
					  }),
			new Ext.Panel({
					  title:"���3",
					  height:30,
						  html:'I love you xr,wait... I sure you is mine 3'
		              })
		]
	  });
        panel1.render("div1");                         //��ʾ����� DIV


3.3  �������������


       �ο� ext /docs/index.html


3.5  Extjs ������¼�����

ExtJS �ṩ��һ��ǿ����¼�������ƣ�ͨ����Щ�¼������������Ӧ�û��Ķ�������
�ؿؼ�״̬�仯�����¿ؼ���ͼ��Ϣ������������н����ȵȡ��¼�ͳһ��
Ext.EventManager ��������������W3C ��׼�¼�����Event ���Ӧ��Ext ��װ��һ��
Ext.EventObject �¼�����֧���¼��������(��ӿ�)ΪExt.util.Observable�����Ǽ̳и���
��������඼֧��������������¼�������Ӧ���ܡ�



HTML���� 

<script>
function a()
{
alert('some thing');
}
window.onload=function(){
document.getElementById("btnAlert").onclick=a;                  //��׼HTML�ĵ� �¼����� �ĵ�������ʱ Ϊ input�趨 �¼�����
}
</script>
<input id="btnAlert" type="button" value="alert��" />


Ext �¼��������ƻ���
----------------------------click�¼�---------------------------------------------------------
<script  type="text/javascript">
 
   function a(){ 
     Ext.Msg.alert("love","i sure you is mine");
   }

  Ext.onReady( function() {      
	 Ext.get("btnAlert").addListener("click",a);                      // ��ȡԪ������ �¼�  (addListener  ��д on)
         Ext.get("btndelay").on("click",a,this,{delay:2000});         //�ӳ�ʱ��ִ��
	});
	<input  id="btnAlert" type="button" value="onclick�¼�"/>
	<input  id="btndelay" type="button" value="delay �ӳ�"/>
</script> 

----------------------------beforedestroy ����ǰ�¼�---------------------------------------------------------
function show(){ 
	 var win =  new Ext.Window( {
	  title:"win",
      width:500,
	  height:300,
      html:'�ر����ǲ����ܵģ�����.......'
	  });   
	  win.addListener("beforedestroy",function (obj){ 
	      obj.show();
		    Ext.Msg.alert("(*^__^*)","�ز��˰ɣ�������.... ");
	       return false; 
	  });
	  win.show();
   }

----------------------------------------------------------------------------------------------------------------

>>>>>>>>>>>>>>>>>>>>>�����¡�ʹ�����>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
 
4.1 Panel    (0400)
     ��������¼���������ɣ�һ��������������һ���ײ������������ͷ�������β����
��������򼸸����������������л����������չ�����رյȹ��ܣ����ṩһϵ�п���
�õĹ��߰�ťʹ�����ǿ�������ʵ���Զ������Ϊ�������Է��������κ������У���屾
����һ���������������ֿ��԰����������������
	new Ext.Panel({
		renderTo:"div1",
	    title:"���header",
		width:400,
	    height:300,
       
		html:'���������',
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
//��嶥����������header--tools��
		new Ext.Panel({
		renderTo:"div2",
	         title:"���header",
		width:400,
	          height:300, 
		html:"<h1>Hello,easyjf open source!</h1>",
		tools:[
			{id:"help",handler:function(){Ext.Msg.alert("help","please help me !")}},
			{id:"save"},
			{id:"close"}
		],
                   tbar:[{pressed:true,text:"ˢ��"}]
		});

//��幤����ʹ�÷���(tbar--Toolbar)
        new Ext.Panel({
		renderTo:"div3",
	         title:"���header",
		width:400,
	         height:300, 
		html:"<h1>Hello,easyjf open source!</h1>",
	          tbar:[
		new Ext.Toolbar.TextItem("������:"),
                    {xtype:"tbfill"},             //�հ�
                    {pressed:true,text:'���'},
                    {xtype:"tbseparator"} ,  //�ָ���
                    {pressed:true,text:'����'} , 
		 {xtype:"tbbutton"},
                    {pressed:true,text:'��ť'} 
                    ]
   }); 
----------------------------------------------------------------------------------------------------------
4.2 ѡ���tabpanel  (0500)
Viewport ����Ҫ��ָ��renderTo��������Ҳ����Viewport ȷʵ����������������ʾ��
�򣬲��������������ʾ�����С�ĸı���ĸ�,Viewport ��Ҫ����Ӧ�ó���������棬
����ͨ��ʹ�ò�ͬ�Ĳ����������ͬ����Ӧ�ó��������档��Viewport �ϳ��õĲ���
��fit��border �ȣ���Ȼ����Ҫ��ʱ����������Ҳ�᳣�á�������Ĵ��룺


//��ͨ����
Ext.onReady(function(){
    new Ext.Viewport({
        enableTabScroll:true,
        layout:"fit",
        items:[{title:"���",
        html:"",
        bbar:[
	   {text:"��ť1"},
            {text:"��ť2"}]
       }]
    });
});

//����һ�����˵��������岼��
Ext.onReady(function(){
       new Ext.Viewport({
             enableTabScroll:true,
              layout:"border",
              items:[
	                  {region:"north",height:50,html:"<h1>��վ��̨����ϵͳ!</h1>"},
				      {title:"menu",region:"west",width:200,collapsible:true,html:"<h1>�˵���</h1>"},    // collapsible���� ���������˵�
		                      {xtype:"tabpanel",region:"center",
				             items:[
				                 {title:"tabpanel1"} ,
						 {title:"tabpanel2"}
			                 ]
		   }                     
               ]
      });
});

>>>>>>>>>>>>>>>>>>>>>�����¡����ڼ��Ի���>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
 
5.1�����ڻ���Ӧ��
ExtJS �д�������Ext.Window �ඨ�壬����̳���Panel����˴�����ʵ��һ�������
���Panel�����ڰ����˸��������϶����ɹرա���󻯡���С�������ԡ�������Ĵ��룺











