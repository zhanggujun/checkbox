##	JS模拟checkebox、radio和select下拉框
###	依赖
*	依赖于jQuery
###	使用方法
*	Clone到本地
*	项目目录中放入font文件夹和vv.js、vv.css
*	页面中引入vv.js和vv.css
*	实例对象：new WM.checkBox();
###	单选和复选
*	属性
	*	id：需要挂载的dom的id
	*	group：生成option的数据（数组格式）
	*	multiple：是否多选（布尔值，默认false）
	*	notNull：是否为空（布尔值，默认false）
	*	checked：初始化被选中的选项（数组格式）
	*	disabled：被禁用的选项（数组格式）
	*	onChange：发生改变时触发的回掉（函数）
*	方法
	*	getCheck：获取被选中项的值和下标（json格式 value表示被选中项的值 index表示被选中项的下标 没有则为null）
	*	getBool：获取所有数据对应的布尔值 被选中为 true 否则为false
*	示例<br>
```
    var checkBox = new WM.checkBox({
        id:'box1', // 需要挂载的dom的id
        group:['数据1','数据2','数据3','数据4','数据5','数据6'], // 数据 数组格式
        multiple:true,  // 是否多选 true--多选 false--单选 默认false
        notNull:true, // 是否不能为空 true--必须选中一个 false--可以都不选 默认false
        checked:[0,'数据3'], //初始化被选中项目 --参数为数据下表或者对应的数据 数组
        disabled:[1,'数据6'], //被禁用的选项 --参数为数据下表或者对应的数据 数组
        onChange:function(){ // 当发生改变时触发的回调函数
            var value = this.getCheck();
            console.log(value);
        }
    });
    $(Element).click(function(){
        var value = checkBox.getCheck();
        var bool = checkBox.getBool();
        console.log(value);
        console.log(bool);
    }); 
```
###	下拉框
*	属性与方法和单选复选差不多。
*	示例<br>
```
    var select = new WM.select({
        id:'box2',
        title:'select',
        //options:['数据1','数据2','数据3'], 数据 参数为数组
        options:(function(){
            var arr = [];
            for(var i=0;i<20;i++){
                arr.push('第'+i+'条数据');
            }
            return arr;
        })(),
        //checked:[0],
        //disabled:true
        selected:[1,3],
        onChange:function(){
            console.log(this.getCheck());
        }
    });
    // getCheck取值 json checkValue--被选中项的数据 checkIndex--被选中项的下表 没有则为null
    var val = select.getCheck();
    console.log(val); // null
```