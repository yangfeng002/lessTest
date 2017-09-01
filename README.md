学习less,css的预编译处理语言
一、学会使用koala工具编译less文件
二、.注释方式  /*多行注释方式---可以编译到css文件中*/      //单行注释不会保存到css文件中
三、变量
   如下定义：@test:20px;
   如下使用：.box{width:@test;}
四、混合 mixin
    1.先定义一个样式，然后其他的可以直接拿过来引用
    .box{
      width:@test_width;
      height:@test_width;
      background: #dbdd5c;
      .border; //混合用法（可以拿过来其他的直接使用）
    }
    .border{ border: 5px solid #ffb2b3;}

    2.混合（可以带参数）
    //混合带参数用法
    .border_02(@border_width){
       border: @border_width solid #ffa3db;
    }
    .test-hunhe{
       .border_02(10px);
    }
   3.//混合带参数有默认值
     .border_03(@border_width:10px){
        border: @border_width solid #ddd;
     }
     .test-hunhe{
       .border_03();
     }

五、匹配模式
        //匹配模式
        .triangle(top,@w:5px,@c:red){
           border-width: @w;
           border-color: transparent transparent @c transparent;
           border-style:dashed dashed solid dashed;
        }
        .triangle(bottom,@w:5px,@c:red){
          border-width: @w;
          border-color: @c transparent transparent  transparent;
          border-style:solid dashed dashed  dashed;
        }
        .triangle(left,@w:5px,@c:red){
          border-width: @w;
          border-color: transparent @c transparent  transparent;
          border-style:dashed solid dashed  dashed;
        }
        .triangle(right,@w:5px,@c:red){
          border-width: @w;
          border-color:  transparent transparent  transparent @c;
          border-style: dashed dashed  dashed solid;
        }
        //这种写法默认匹配的时候都会添加的样式
        .triangle(@_,@w:5px,@c:#ccc){
          width:0;
          height: 0;
          overflow:hidden;
        }
        .sanjiao{
           .triangle(top,100px);
        }
 六、运算（+ - * /）
 @test0:30px;//运算
 .yunsuan{
    //width: @test0+20;//注意加法运算的时候不能有空格
    width:(@test0 - 10)*2;//减法要有空格
    //color:#ccc;
   color:#ccc -10;//颜色值会转换
 }

七、嵌套
/*嵌套*/
.list{
   width:400px;
   margin: 10px auto;
   padding: 0;
   list-style: none;
  li{
    height: 30px;
    line-height: 30px;
    background-color: #dbdd5c;
    margin-bottom: 5px;
  }
  a{
    float: left;
    &:hover{
      color: red;
    }
  }
  &_nav{
    //可以获取上一级相同的名称
  }
  span{
    float: right;
  }
}

八、arguments使用

九、避免编译




