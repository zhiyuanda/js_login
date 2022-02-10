# HTML+CSS+JS案例展示(模态框显示移动与隐藏)
>   参考来源：
>
> [JavaScript基础语法-dom-bom-js-es6新语法-jQuery-数据可视化echarts黑马pink老师前端入门基础视频教程(500多集)持续_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1Sy4y1C7ha?p=244&spm_id_from=pageDriver)
##  效果展示：

![img](https://img-blog.csdnimg.cn/ac55f525a162474ab2cb5917fd678795.gif)


## 网页GitHub地址如下：（若加载较慢建议刷新后耐心等待一会~）

[js_login](https://jiang-lijun.github.io/js_login/)

## 主要功能：

1. 点击弹出模态框以及全屏灰色背景
2. 点击关闭按钮，隐藏模态框以及背景
3. 在模态框的头部按下鼠标开始移动，松开鼠标停止移动模态框

## 网页代码如下：

### HTMLHTML+CSS+JS：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>js_login</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        a {
            text-decoration: none;
            color: #000;
        }
        .login {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            width: 500px;
            height: 218px;
            border: 1px solid #ccc;
            background-color: #fff;
            transform: translate(-50%,-50%);
            box-shadow: 0 0 20px #ddd;
            z-index: 9999;
        }
        .login-header {
            float: left;
            width: 100%;
            height: 100%;
            line-height: 40px;
            margin: 0 auto;
            text-align: center;
            font-weight: 700;
            font-size: 16px;

            color: #000;
        }
        .login-header a {
            display: block;
            margin: 0 auto;
        }
        .login-title {
            cursor: move;
            position: relative;
            text-align: center;
            font-size: 18px;
            height: 40px;
            line-height: 40px;
        }
        .login-title span{
            position: absolute;
            width: 40px;
            height: 40px;
            top: -20px;
            right: -30px;
            font-size: 12px;
            border: 1px solid #ebebeb;
            background-color: #fff;
            border-radius: 50%;
        }
        .login-bd {
            height: 108px;
        }
        .login-input {
            float: right;
            margin-right: 50px;
            height: 50px;
            line-height: 67px;
            font-size: 12px;
        }
        input {
            right: 50px;
            border: 1px solid #ccc;
            width: 370px;
            height: 30px;
        }
        .login-btn {
            margin: 15px 125px;
            font-size: 12px;
            width: 250px;
            height: 30px;
            line-height: 30px;
            border: 1px solid #ccc;
            text-align: center;
        }
        .login-bg {
            display: none;
            width: 100%;
            height: 1000px;
            background-color: gray;
            z-index: 1;
        }
    </style>
</head>
<body>
    <div id="login-header" class="login-header">
        <a href="javascript:;">点击弹出登录框</a>
    </div>
    <div id="login" class="login">
        <div class="login-title">登陆会员<span><a href="javascript:;" class="closebtn">关闭</a></span></div>
        <div class="login-bd">
            <div class="login-input">
                <label>用户名：</label>
                <input type="text" placeholder="请输入用户名" name="info[username]" id="username">
            </div>
            <div class="login-input">
                <label>登陆密码：</label>
                <input type="password" placeholder="请输入密码" name="info[password]" id="password">
            </div>
        </div>
        <div id="login-btn" class="login-btn">
            <a href="javascript:;">登录会员</a>
        </div>
    </div>
    <div id="bg" class="login-bg"></div>
    <script>
        //1. 获取元素
        var login = document.querySelector('.login');
        var bg = document.querySelector('.login-bg');
        var header = document.querySelector('.login-header');
        var closebtn = document.querySelector('.closebtn');
        var title = document.querySelector('.login-title');
        //2. 注册事件
        //2.1 点击弹出模态框以及全屏灰色背景
        header.addEventListener('click',open);
        function open() {
            login.style.display = 'block';
            bg.style.display = 'block';
        };
        //2.2 点击关闭按钮，隐藏模态框以及背景
        closebtn.addEventListener('click',close);
        function close() {
            login.style.display = 'none';
            bg.style.display = 'none';
        }
        //2.3 在模态框的头部按下鼠标开始移动，松开鼠标停止移动模态框
        title.addEventListener('mousedown',function(e){
            var x = e.pageX - login.offsetLeft;
            var y = e.pageY - login.offsetTop;
            document.addEventListener('mousemove',move);
            function move(e) {
                if((e.pageX - x) > 250 && (e.pageY - y) > 105){
                    login.style.left = e.pageX - x + 'px';
                    login.style.top = e.pageY - y + 'px';
                }
            }
            document.addEventListener('mouseup',function() {
                this.removeEventListener('mousemove',move);
            })
        });

    </script>
</body>
</html>
```
