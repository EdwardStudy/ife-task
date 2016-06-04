# 任务四：定位和居中问题

1. 资料笔记

 [定位详解](http://www.w3cplus.com/css/advanced-html-css-lesson2-detailed-css-positioning.html)：从浮动到定位。
 
  浮动可以让元素一个一个挨着，创建一个**自然流布局**，同时允许设置元素的自身尺寸和服元素容器的尺寸大小。
  
  浮动元素需要考虑父元素塌陷的问题。清除浮动影响的原因。
  
  兄弟元素添加空标签 'clear: both' ，不适合语义化
  
  父元素设置 'overflow: auto;' 副作用 添加滚动条 或者 'overflow: hidden;' 更好 。但是添加其他样式延续到父容器外部时会被截断在父元素内部。
  
  clearfix 在父元素添加伪类 :before :after。:before防止子元素顶部外边距坍塌（外边距重叠）。对于IE6/7，使用"display: table"创建一个匿名"table-cell"。
  :after放置底部外边距坍塌，以及用来清除元素的浮动。还需加上 "*zoom" 通过依靠计算布局清理浮动的 haslayout 特性仅在 IE 6/7 中存在. haslayout特性可以从新计算布局清理幅度。
  
  position
  
  * static 无法设置 “top、right、bottom、left”
  * relative 可以设置位移“top、right、bottom、left”。从默认位置移动，其在页面中仍是正常的、静态的，仍属于自然流。其最初位置不会被其他元素占用
  * absolute 可以设置位移，脱离文档流。祖先元素设置了相对定位和绝对定位，其起始位置为这个祖先元素。
  * fixed 可以设置位移，定位设置为相对于浏览器窗口，其他和absolute一致。 可以用来设置页头页尾。 footer { bottom: 0; left: 0; right: 0; position: fixed; }
  
  
  z-index DOM默认元素在顶部的要低于底部的。需要先脱离文档普通流 （ position: relative absolute fixed ）
  
  [居中](https://css-tricks.com/centering-css-complete-guide/)：
  
  水平居中： 
  
  inline/inline-*: 在block级别的父元素上使用水平居中 { text-align: center; }
  
  单个block: 这是block元素宽度 通过 margin-left margin-right 设置 auto { margin: 0 auto; }
  
  多个block：上述方法可以是多个block元素并列展示，而会使用flex 布局可以并排居中 { display: flex; justify-content: center; } //居中
  
  垂直居中：
  
  inline/inline-*: 1.) 使用padding-top、padding-bottom，如果padding不能用就使用 lin-height = hieght并且处理留白white-space为nowrap。
  多行情况下可使用padding就设置padding。2) 否则如文本所在元素为table cell，使用vertical-align = middle（这里将垂直对齐，而不是水平对齐） 3) 使用display: flex;，在 flex容器上设置 flex-direction: column (注意容器需要固定高度) 4).伪类 100%高 方法没看明白
  
  block: 1.) 知道高度的方法 relative > absolute, 内部 top:50%; margin-top: - { height / 2 } px; 考虑box-sizing，如果不是border-box则需要考虑padding、border（添加）。 2).不知道高度 使用translateY可能可以居中 { top: 50%; transform: translateY(-50%); } 3). 使用 flexbox { display: flex; flex-direction: column; justify-content: center; }
  
  水平垂直居中：
  1). 知道宽度 高度 使用 margin 百分符设置上和左 margin 位置 { margin: -{ height / 2 } px 0 0 -{ width / 2 }px; top: 50%; left: 50%; } 考虑盒子模型中的是否包含 border
  
  2). 不知道高宽 { top: 50%; left: 50%; transform: translate(-50%, -50%);  }
  
  3). 使用 flexbox   { display: flex; flex-direction: column; justify-content: center; }