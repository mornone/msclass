<H3>入门</H3>
<P>想要使用这款组件，需要页面引入 <A href="MSClass.js">MSClass.js</A> 核心文件，该文件在您的HTML文档<CODE>&lt;head&gt;</CODE>标签之内。</P>
<textarea rows="2" readonly>&lt;script type="text/javascript" src="/path/MSClass.js"&gt;&lt;/script&gt;</textarea>
<P>参数直接赋值法：</P><textarea rows="5" readonly>&lt;script type="text/javascript"&gt;
  new Marquee(&quot;Marquee&quot;,0,1,760,104,50,5000,3000,52)
	new Marquee(&quot;Marquee&quot;,null,null,760,104,null,5000,null,-1)
&lt;/script&gt;
</textarea>
<P>参数动态赋值法：</P><textarea rows="12" readonly>&lt;script type="text/javascript"&gt;
	var Marquee1 = new Marquee(&quot;Marquee&quot;) *此参数必选
	Marquee1.Direction = &quot;top&quot;; 或者 Marquee1.Direction = 0;
	Marquee1.Step = 1;
	Marquee1.Width = 760;
	Marquee1.Height = 52;
	Marquee1.Timer = 50;
	Marquee1.DelayTime = 5000;
	Marquee1.WaitTime = 3000;
	Marquee1.ScrollStep = 52;
	Marquee1.Start();
&lt;/script&gt;
</textarea>
<P>对象直接赋值法：</P><textarea rows="15" readonly>&lt;script type="text/javascript"&gt;
	new Marquee(
	{
		MSClass	  : {MSClassID :  &quot;MSClassBox &quot; , ContentID :  &quot;ContentID &quot; , TabID :  &quot;TabID &quot;},
		Direction : &quot;top&quot;,
		Step : 0.1,
		Width : 760,
		Height : 52,
		Timer : 50,
		DelayTime : 5000,
		WaitTime : 3000,
		ScrollStep: 52,
		AutoStart : 1
	});
	
	
	
	new Marquee(
	{
		MSClassID :  &quot;MSClassBox &quot;,
		ContentID :  &quot;ContentID &quot;,
		TabID :  &quot;TabID &quot;,
		Direction : &quot;top&quot;,
		Step : [0.5,30],
		Width : 760,
		Height : 52,
		Timer : 50,
		DelayTime : 5000,
		WaitTime : 3000,
		ScrollStep: 52,
		AutoStart : 1
	});
	
	
	new Marquee(
	{
		MSClass : [&quot;MSClassBox &quot;,&quot;ContentID &quot;,&quot;TabID &quot;],
		Direction : &quot;top&quot;,
		Step : [0.4,&quot;easeOutElastic&quot;],
		Width : 760,
		Height : 52,
		Timer : 50,
		DelayTime : 5000,
		WaitTime : 3000,
		ScrollStep: 52,
		AutoStart : 1
	});
&lt;/script&gt;
</textarea>
<H4>使用建议：</H4>
<UL>
	<LI>对于复杂/高级应用推荐使用&quot;&lt;b&gt;对象直接赋值法&lt;/b&gt;&quot;创建应用实例</LI>
	<LI>对于DIV+CSS(UL+LI)应用中，若文字不可见请先尝试指定LI的字体大小</LI>
	<LI>建议直接赋予容器的显示区域的宽度和高度，如(&lt;div id=&quot;Marquee&quot; style=&quot;width:760px;height:52px;&quot;&gt;......&lt;/div&gt;)</LI>
	<LI>建议为容器添加样式overflow = auto，如(&lt;div id=&quot;Marquee&quot; style=&quot;width:760px;height:52px;overflow:auto;&quot;&gt;......&lt;/div&gt;)</LI>
	<LI>为了更准确的获取滚动区域的宽度和高度，请尽可能将各滚动单位直接赋予正确宽高度</LI>
	<LI>对于TABLE标记的横向滚动，需要对TABLE添加样式display = inline，如(&lt;div id=&quot;Marquee&quot; style=&quot;width:760px;height:52px;overflow:auto;&quot;&gt;&lt;table style=&quot;display:inline&quot;&gt;......&lt;/table&gt;&lt;/div&gt;)</LI>
	<LI>对于翻屏滚动或间歇滚动，要注意各滚动单位间的间距，同时需要对容器的可视高度和可视宽度做好准确的设置，对于各滚动单位间的间距可以通过设置行间距或者单元格的高宽度来进行调整</LI>
	<LI>若对于UL、LI自动换行的样式设置问题上存在困难，建议将其转换成表格(TABLE)的形式来达到同等的效果</LI>
	<LI>针对横向滚动的文字段落，如果最末端是以空格&quot; &quot;结束的，请将空格&quot; &quot;转换成&quot;&amp;nbsp;&quot;</LI>
	<LI>鼠标悬停滚动思想源自Flash，所以有一定的局限性(容器内仅允许用图片&lt;img&gt;或者带链接的图片&lt;a&gt;&lt;img&gt;&lt;/a&gt;的形式，并需要禁止其自动换行)</LI>
	<LI>若用户有隐藏区域的应用(display=none)，应在此脚本生效后，动态将该区域设置成不显示方可生效，或者通过&quot;对象直接赋值法&quot;将隐藏区域ID传递给HiddenID</LI></UL>
<H3>配置</H3>
<P>MSClass相关参数如下： </P>
<TABLE width="100%">
  <THEAD>
  <TR>
    <TH>属性</TH>
    <TH>类型</TH>
    <TH>默认</TH>
    <TH>描述</TH></TR>
  <TR>
    <TD>ID</TD>
    <TD>string</TD>
    <TD>必需</TD>
    <TD>容器ID，通过new Mraquee(&quot;&quot;)第一个参数指定ID</TD></TR>
  <TR>
    <TD>Direction</TD>
    <TD>integer</TD>
    <TD>0</TD>
    <TD>滚动方向(默认为0向上滚动) 值:0上 1下 2左 3右 -1上下交替 4左右交替</TD></TR>
  <TR>
    <TD>Step</TD>
    <TD>integer/array</TD>
    <TD>2</TD>
    <TD>滚动的步长(数值越大,滚动越快,小于1切换为缓动。若为数组[0.5,20]形式，则可设置Tween的缓动类别,0.5为系数，20为缓动类别)</TD></TR></THEAD>
  <TBODY>
  <TR>
    <TD>Width</TD>
    <TD>integer</TD>
    <TD>容器初始设置的宽度</TD>
    <TD>容器可视宽度(默认值为容器初始设置的宽度)</TD></TR>
  <TR>
    <TD>Height</TD>
    <TD>integer</TD>
    <TD>容器初始设置的高度</TD>
    <TD>容器可视高度(默认值为容器初始设置的高度)</TD></TR>
  <TR>
    <TD>Timer</TD>
    <TD>integer</TD>
    <TD>30</TD>
    <TD>定时器，即频率/执行周期(默认值为30,数值越小,滚动的速度越快,1000=1秒,建议不小于20)</TD></TR>
  <TR>
    <TD>DelayTime</TD>
    <TD>integer</TD>
    <TD>0</TD>
    <TD>间歇停顿延迟时间(默认为0不停顿,1000=1秒)</TD></TR>
  <TR>
    <TD>WaitTime</TD>
    <TD>integer</TD>
    <TD>0</TD>
    <TD>开始时的等待时间(默认或0为不等待,1000=1秒)</TD></TR>
  <TR>
    <TD>ScrollStep</TD>
    <TD>integer</TD>
    <TD>0</TD>
    <TD>间歇滚动间距(默认为翻屏宽/高度,该数值为-2，DelayTime为0则为鼠标悬停控制,-1禁止鼠标控制)</TD></TR>
  <tr>
    <TD>SwitchType</TD>
    <TD>integer</TD>
    <TD>0</TD>
    <TD>轮显类型(默认为0滚动,可选值1切入,2渐显)</TD>
	</tr>
  <TR>
    <TD>HiddenID</TD>
    <TD>string/array</TD>
    <TD>null</TD>
    <TD>隐藏区域ID(可选,如果隐藏区域只有一层，可以用&quot;hiddenid&quot;的形式，如果多层，请用数组[&quot;hiddenid1&quot;,&quot;hiddenid2&quot;]的形式全包含进去)</TD></TR>
  <TR>
    <TD style="background-color: #D8D8D8" colspan="4"><STRONG>
	注意：以上参数针对直接赋值法应用有先后顺序之分，如：new 
	Marquee(&quot;Marquee&quot;,0,1,760,104,20,5000,0,0,0,[&quot;hiddenid1&quot;,&quot;hiddenid2&quot;])</STRONG></TD>
    </TR>
  <tr>
    <TD>MSClassID</TD>
    <TD>string</TD>
    <TD>针对对象赋值必需</TD>
    <TD>容器ID</TD>
	</tr>
	<tr>
    <TD>ContentID</TD>
    <TD>string</TD>
    <TD>UL+LI、DL+DT+DD必需</TD>
    <TD>针对DIV+CSS的应用，属显示容器内的内容区域ID，即实际内容容器UL或DL的ID。</TD>
	</tr>
	<tr>
    <TD>TabID</TD>
    <TD>string/array</TD>
    <TD>页码/TAB的ID</TD>
    <TD>可选，如果需要页码/TAB支持，将相关ID传递进来即可，若多个Tab应用请以数组形式传递，如：[&quot;tabid1&quot;,&quot;tabid2&quot;]。</TD>
	</tr>
	<tr>
    <TD>TabEvent</TD>
    <TD>string</TD>
    <TD>onmouseover</TD>
    <TD>可选，针对页码/TAB鼠标响应方式，默认&quot;onmouseover&quot;，鼠标划过即切换(可选值:&quot;onclick&quot;)</TD>
	</tr>
	<tr>
    <TD>TabTimeout</TD>
    <TD>integer</TD>
    <TD>鼠标响应延迟时间</TD>
    <TD>可选，针对页码/TAB鼠标响应延迟时间，鼠标响应事件(TabEvent)在设定时间后方有效。</TD>
	</tr>
	<tr>
    <TD><b>MSClass</b></TD>
    <TD>array/object</TD>
    <TD>若设置此项，则<br>
	以上5项不需要设置</TD>
    <TD>快速设置：[&quot;MSClassID&quot;,&quot;ContentID&quot;,&quot;TabID&quot;,&quot;TabEvent&quot;,200]分别对应上述相关参数,不需要的参数省略不写即可，如[&quot;MSClassID&quot;,&quot;ContentID&quot;]；<p>
	{MSClassID:&quot;MSClassID&quot;,ContentID:&quot;ContentID&quot;,TabID:&quot;TabID&quot;,TabTimeout:200}分别对应上述相关参数,不需要的参数省略不写即可。</TD>
	</tr>
	<tr>
    <TD>ContextMenu</TD>
    <TD>array</TD>
    <TD>&nbsp;</TD>
    <TD>右键菜单相关，可选 
	，默认关闭，格式:[1,[&quot;menu1&quot;],[],[&quot;menu2&quot;,&quot;fn()&quot;]]。(0/1,开启/关闭；[&quot;menu1&quot;]不可点击，[]分隔线,[&quot;menu2&quot;,&quot;fn()&quot;]可点击及点击事件)</TD>
	</tr>
	<tr>
    <TD>PrevBtnID</TD>
    <TD>string</TD>
    <TD>&nbsp;</TD>
    <TD>执行下一次滚动的元素ID，可选，针对间歇滚动有效</TD>
	</tr>
	<tr>
    <TD>NextBtnID</TD>
    <TD>string</TD>
    <TD>&nbsp;</TD>
    <TD>执行上一次滚动的元素ID，针对间歇滚动有效</TD>
	</tr>
	<tr>
    <TD>AutoStart</TD>
    <TD>boolean</TD>
    <TD>针对对象赋值有效</TD>
    <TD>针对对象赋值设置是否使应用自动执行(省去Start步骤)。可选值：0,1,true,false</TD>
	</tr>
  </TBODY></TABLE>
<H3>致谢</H3>
