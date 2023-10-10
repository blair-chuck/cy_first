本项目shop——vue3是前端部分，serve是后端部分，前端部分是独立完成编写的。

商店后台管理系统															  
项目描述：
 管理员通过账号密码验证进入后台系统，可以对用户信息进行增删改查操作。对角色列表进行管理。对商品通过搜索关键字进行查找，实现用户以及商品的管理。
技术栈：Vue3+Vue-cli+Element-plus+Axios
实现过程：
1、使用Vue-router实现路由之间的跳转。路由守卫实现登录信息验证后的跳转功能。验证token进行路由拦截，防止未登录用户进入后台。
2、使用 Vuex管理数据，实现登录信息的管理。
3、使用Element-plus和Flex实现响应式页面布局。
4、通过封装Axios实现页面局部更新，拦截器进行表单验证，验证成功进行Axios请求。

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        form{
            display: flex;
            flex-direction: column;
            flex-wrap:wrap;
            justify-content: space-between;
            align-content: space-around;
        }

       li{
        list-style: none;
       }
    </style>
</head>
<body>
        <form name="my">
        姓名：<input type="text" placeholder="请输入：">
        手机：<input type="text" placeholder="请输入：" name="mytel" onblur="gettel()">
        地区：<select name="" id="" class="area">
            <option value="">北京</option>
            <option value="">上海</option>
            <option value="">广州</option>
            <option value="">南京</option>
            <option value="">成都</option>
        </select>
        身份证：<input type="text" placeholder="请输入："  name="credit" onblur="getid()">
        性别：<input type="text" placeholder="请输入：" name="creditsex" class="sex">
        朋友人数：<input type="text" placeholder="请输入：" name="myform"  onblur="getfri()">
        <ul>
            
        </ul>
        </form>
    
    <script>
        //朋友人数
        let ul =document.querySelector('ul')
        function getfri(){
            
            let li=ul.childNodes
            if(li){
               for(let i=li.length-1 ;i>=0; i--){
                ul.removeChild(li[i])
               }
            }
            let num=my.myform.value
            if(num >=1 && num <=20){
                for(let j=1 ;j<=num; j++ ){
                    let li =document.createElement('li')
                    ul.appendChild(li)
                    li.innerHTML=`朋友${j}:<input type="text">`
             }
            
            }else{
                alert('朋友人数不可少于1或多于20 人')
            }
        }
  
        //身份识别
        let sex =document.querySelector('.sex')
        function getid(){

            let idnum =my.credit.value 
            let reg18= /^(([1-6][1-9]|50)\d{4}(18|19|20)\d{2}((0[1-9])|10|11|12)(([0-2][1-9])|10|20|30|31)\d{3}[0-9Xx])$/
            if(!reg18.test(idnum)){
                alert('身份证格式不对')
            }else {
                if(parseInt(idnum.substr(16, 1)) % 2 === 1 ){
                    my.creditsex.value ='男'
                }else{
                    my.creditsex.value ='女'
        }
      }
    }
  

    //手机号
    function gettel(){
        let regtel =/^1(3\d|4[5-9]|5[0-35-9]|6[567]|7[0-8]|8\d|9[0-35-9])\d{8}$/
        let telnum = my.mytel.value
        // telnum =''
        if(!regtel.test(telnum)){
            alert('手机号格式错误')
           
        }
        
    }
    </script>
</body>
</html>
