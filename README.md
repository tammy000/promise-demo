本文为转载，方便自己查看原理

1、什么是promise？

　　Promise可能大家都不陌生，因为Promise规范已经出来好一段时间了，同时Promise也已经纳入了ES6，而且高版本的chrome、firefox浏览器都已经原生实现了Promise，只不过和现如今流行的类Promise类库相比少些API。

　　所谓Promise，字面上可以理解为“承诺”，就是说A调用B，B返回一个“承诺”给A，然后A就可以在写计划的时候这么写：当B返回结果给我的时候，A执行方案S1，反之如果B因为什么原因没有给到A想要的结果，那么A执行应急方案S2，这样一来，所有的潜在风险都在A的可控范围之内了。

Promise规范如下：

一个promise可能有三种状态：等待（pending）、已完成（fulfilled）、已拒绝（rejected）
一个promise的状态只可能从“等待”转到“完成”态或者“拒绝”态，不能逆向转换，同时“完成”态和“拒绝”态不能相互转换
promise必须实现then方法（可以说，then就是promise的核心），而且then必须返回一个promise，同一个promise的then可以调用多次，并且回调的执行顺序跟它们被定义时的顺序一致
then方法接受两个参数，第一个参数是成功时的回调，在promise由“等待”态转换到“完成”态时调用，另一个是失败时的回调，在promise由“等待”态转换到“拒绝”态时调用。同时，then可以接受另一个promise传入，也接受一个“类then”的对象或方法，即thenable对象。

2.promise原理分析

　　可以看到promise的规范并不是很多，下面我们一边分析promise一边自己写一个promise的实现。Promise实现的大致思路如下：

　　构造函数Promise接受一个函数resolver，可以理解为传入一个异步任务，resolver接受两个参数，一个是成功时的回调，一个是失败时的回调，这两参数和通过then传入的参数是对等的。

其次是then的实现，由于Promise要求then必须返回一个promise，所以在then调用的时候会新生成一个promise，挂在当前promise的_next上，同一个promise多次调用都只会返回之前生成的_next。

3，做一个demo，异步获取一个json配置，解析json数据拿到里边的图片，然后按顺序队列加载图片，每张图片加载时给个loading效果。

4.标准的Promise

　　可参考html5rocks的这篇文章JavaScript Promises，目前高级浏览器如Chrome、Firefox都已经内置了Promise对象，提供更多的操作接口，比如Promise.all()，支持传入一个promises数组，当所有promises都完成时执行then，还有就是更加友好强大的异常捕获，应对日常的异步编程，应该足够了。
现今流行的各大js库，几乎都不同程度的实现了Promise，如dojo，jQuery、Zepto、when.js、Q等，只是暴露出来的大都是Deferred对象,当然还有angularJs中的$q.这里以jQuery为例，说一下：


// animate  
$('.box')  
    .animate({'opacity': 0}, 1000)  
    .promise()  
    .then(function() {  
        console.log('done');  
    });  
  
// ajax  
$.ajax(options).then(success, fail);  
$.ajax(options).done(success).fail(fail);  
  
// ajax queue  
$.when($.ajax(options1), $.ajax(options2))  
    .then(function() {  
        console.log('all done.');  
    }, function() {  
        console.error('There something wrong.');  
    });  
