##  Angular

### 代码说明

1. ng-app:

   `<html ng-app="模块名">` 

   ```
   var myAppModule = angular.module('模块名',[]);
   ```

   ng-app属性,用来告诉页面哪一部分需要使用angular管理.通常情况下都这样管理，可以加在任何元素上.

   一个页面里只能有一个ng-app，不能有多个，不同的页面可以运用不同的ng-app模块，但是可以在同一个js里定义多个模块

   angular.module()中的第二个参数是必须是一个数组,用于定义该模块依赖的模块,数组的值是字符串,也就是依赖的模块的名字.一旦写入了依赖的模块,那么该模块也就拥有了依赖的模块的指令,方法,等...

2. ng-controller:

   `<div ng-controller="CarController">` 

   使用一个控制器来控制页面中的某个区域,这里就是管理这个<div>到</div>里的所有内容。这里使用的控制器就是script.js里定义的CarController函数 

3. ng-repeat:

   `<tr ng-repeat="item in items">` 

   循环当前的标签(包括里面的内容和自己),循环中的当前变量就是item,item在当前作用域的items变量里进行循环
   即CarController里定义的$scope.items数组.

    ```
    $scope.items = [
        {"title":"兔子","quantity":1,"price":"100"},
        {"title":"喵","quantity":1,"price":"200"},
        {"title":"狗只","quantity":1,"price":"400"},
        {"title":"仓鼠","quantity":1,"price":"300"}
    ];
    ```

4. {{ }}：

   `<td>{{item.title}}</td>` 

   `ng-bind = "item.title"`

   使用{{}}来动态的绑定视图里显示的数据.{{}}里就是当前作用域里的变量

   ng-bind属性来绑定数据和{{}}来绑定数据,效果一致,
   但是如果有大量的数据,在数据还没有加载完成之前,如果使用{{}},用户会看到{{}},而不是被替换掉的实际数据.所以初始化的数据可以使用ng-bind

5. ng-model:

   `ng-model = "item.quantity"`

   ng-model用在输入框里,使输入的内容和它等于的变量数据进行绑定,
   也就是说,输入的值变化,变量就变化,变量变化,视图上对应显示的数据也变化

6. currency:

   `<td>{{item.price|currency}}</td>`

   `<td>{{item.price*item.quantity|currency}}</td>`

   angular带有过滤器特性,可以用来做文本格式的转换,其中,currency货币过滤器,可以实现美元格式化

7. ng-click:

   `<button ng-click="remove($index)">remove</button>`

   为元素绑定click事件的回调,点击后就调用作用域下的remove方法,也就是在CarController中添加的remove方法

8. $index:

   `remove($index)`

   $index是在ng-repeat过程中的循环的索引值,从0开始

9. 控制器：

   `function CarController ($scope){`

   `}`
   控制器负责管理相关的区域的逻辑.函数的形参$scope就是当前区域的作用域,区域中的变量,方法,都从它的作用域中寻找.
   比如这里的$scope.items和$scope.remove

10. 监测改变：

   `$scope.$watch(watchObj,watchCallback,ifDeep)`

   *watchObj:*

   需要被检测的对象,可以是以下任意一种:

   \1. 某个数据,监测这个数据的值是否发生变化

   \2. 一条angular表达式,监测表达式的结果是否发生变化

   \3. 函数(),监测函数的返回值是否发生变化

   注意,以上三种,无论是哪种,都应该是字符串格式,并且都是在$scope作用域下执行的.

   \4. 函数,非字符串格式,而是直接传入一个函数,可以直接写一个匿名函数,也可以传入一个函数,注意,它不是在$scope作用域下的,所以,如果传入的是当前作用域下的函数,还是需要写:$scope.function

   *watchCallback :*

   接受一个函数或者表达式,当watchObj发生变化是会被调用或执行.

   如果是函数形式,它会收到三个参数:

   watchCallback (newValue,oldValue,scope)

   ​    newValue: watchObj的新的值 

   ​    oldValue: watchObj的旧的值

   ​    scope: 就是当前控制器的$scope

   注意:函数或者表达式不是在$scope作用域下执行的,所以,如果是需要调用当前作用域下的某个函数,应该$scope.watchCallback

   *ifDeep:* 

   一个布尔值

   如果 watchObj 的类型是对象或者数组的时候, ifDeep值设置为true, 那么angular会检测被监控对象的每个属性是否发生了变化,而不只是检测一个简单的值.

   注意,如果是字符串格式,不需要写$scope,比如这里的factorial.number,但如果是变量格式,则必须传入$scope,如`$scope.$watch($scope.factorial.number,$scope.compute)`

最后,$(watch)会返回一个函数,这个函数可以用来销毁该控制器,只需要被调用一次即可:

`var destroy = $scope.$watch(...);`

`destroy()`

11. ng-show:

   ```
   <div class="content" ng-show="ifShow"></div>

    $scope.ifShow = false;
       $scope.toggleShow = function(){
           $scope.ifShow = !$scope.ifShow;
           $scope.text = $scope.text=='点击显示框' ? '点击隐藏框' : '点击显示框'
       }
   ```

   ng-show: 绑定的数据值为true时,显示元素,值为false时,隐藏元素

12. arrayObject.splice(index, howmany, item1, …, itemX)

| 参数              | 描述                                  |
| --------------- | ----------------------------------- |
| index           | 必需。整数，规定添加/删除项目的位置，使用负数可从数组结尾处规定位置。 |
| howmany         | 必需。要删除的项目数量。如果设置为 0，则不会删除项目。        |
| item1, …, itemX | 可选。向数组添加的新项目。                       |

13. ng-class

   ```
   <div class="tip" ng-class="{err:ifErr,warn:ifWarn}" ng-show="ifShow">{{tipText}}</div>
   ```
​      其中,err和warn是待选的类名,":"后面绑定数据,该数据决定了该类名是否会被添    加,如果数据的值为true,该类名会被添加,反之则不会被添加

14.  filter

    过滤器用来对数据进行格式的转换,数据格式的转化与逻辑无关,因此,我们使用过滤器来进行这些操作:

    `{{expression | filter1:,参数1,参数2... | filter2: 参数1,参数2... }}`

    expression : 表达式,也就是还没有经过过滤的变量值,相当于普通的 {{}}里面的内容

    filter1 : 过滤器的名字,可以是angular内置的过滤器,也可以自定义过滤器(在下一篇里讲解)

    参数1,参数2,... : 需要被传递给过滤器函数的参数,可以有多个

    过滤器可以通过 "|" 进行多次过滤``

   ```
myFilter.filter('titleCase',function(){    
    var titlecase = function(title,num){...    
    };    
    return titlecase
});
   ```
.filter的第一个参数为过滤器的名字,也就是在{{}}里面使用的名字,第二个参数是  一个函数,函数需要再返回一个函数,被返回的函数,就是用来处理数据的函数,第一个参数就是需要被过滤的数据,后面的参数,就是在使用过滤器的时候,冒号后面传入的值. 比如这里的1:

```
<span>{{title_1 | titleCase: 1 }}</span> 
```

15. ng-if:

    **ng-if** 指令用于在表达式为 false 时移除 HTML 元素。

    如果 if 语句执行的结果为 true，会添加移除元素，并显示。

    **ng-if** 指令不同于 ng-hide， ng-hide 隐藏元素，而 **ng-if** 是从 DOM 中移除元素。