����Ϊת�أ������Լ��鿴ԭ��

1��ʲô��promise��

����Promise���ܴ�Ҷ���İ������ΪPromise�淶�Ѿ�������һ��ʱ���ˣ�ͬʱPromiseҲ�Ѿ�������ES6�����Ҹ߰汾��chrome��firefox��������Ѿ�ԭ��ʵ����Promise��ֻ��������������е���Promise��������ЩAPI��

������νPromise�������Ͽ������Ϊ����ŵ��������˵A����B��B����һ������ŵ����A��Ȼ��A�Ϳ�����д�ƻ���ʱ����ôд����B���ؽ�����ҵ�ʱ��Aִ�з���S1����֮���B��Ϊʲôԭ��û�и���A��Ҫ�Ľ������ôAִ��Ӧ������S2������һ�������е�Ǳ�ڷ��ն���A�Ŀɿط�Χ֮���ˡ�

Promise�淶���£�

һ��promise����������״̬���ȴ���pending��������ɣ�fulfilled�����Ѿܾ���rejected��
һ��promise��״ֻ̬���ܴӡ��ȴ���ת������ɡ�̬���ߡ��ܾ���̬����������ת����ͬʱ����ɡ�̬�͡��ܾ���̬�����໥ת��
promise����ʵ��then����������˵��then����promise�ĺ��ģ�������then���뷵��һ��promise��ͬһ��promise��then���Ե��ö�Σ����һص���ִ��˳������Ǳ�����ʱ��˳��һ��
then��������������������һ�������ǳɹ�ʱ�Ļص�����promise�ɡ��ȴ���̬ת��������ɡ�̬ʱ���ã���һ����ʧ��ʱ�Ļص�����promise�ɡ��ȴ���̬ת�������ܾ���̬ʱ���á�ͬʱ��then���Խ�����һ��promise���룬Ҳ����һ������then���Ķ���򷽷�����thenable����

2.promiseԭ�����

�������Կ���promise�Ĺ淶�����Ǻܶ࣬��������һ�߷���promiseһ���Լ�дһ��promise��ʵ�֡�Promiseʵ�ֵĴ���˼·���£�

�������캯��Promise����һ������resolver���������Ϊ����һ���첽����resolver��������������һ���ǳɹ�ʱ�Ļص���һ����ʧ��ʱ�Ļص�������������ͨ��then����Ĳ����ǶԵȵġ�

�����then��ʵ�֣�����PromiseҪ��then���뷵��һ��promise��������then���õ�ʱ���������һ��promise�����ڵ�ǰpromise��_next�ϣ�ͬһ��promise��ε��ö�ֻ�᷵��֮ǰ���ɵ�_next��

3����һ��demo���첽��ȡһ��json���ã�����json�����õ���ߵ�ͼƬ��Ȼ��˳����м���ͼƬ��ÿ��ͼƬ����ʱ����loadingЧ����

4.��׼��Promise

�����ɲο�html5rocks����ƪ����JavaScript Promises��Ŀǰ�߼��������Chrome��Firefox���Ѿ�������Promise�����ṩ����Ĳ����ӿڣ�����Promise.all()��֧�ִ���һ��promises���飬������promises�����ʱִ��then�����о��Ǹ����Ѻ�ǿ����쳣����Ӧ���ճ����첽��̣�Ӧ���㹻�ˡ�
�ֽ����еĸ���js�⣬��������ͬ�̶ȵ�ʵ����Promise����dojo��jQuery��Zepto��when.js��Q�ȣ�ֻ�Ǳ�¶�����Ĵ���Deferred����,��Ȼ����angularJs�е�$q.������jQueryΪ����˵һ�£�


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
