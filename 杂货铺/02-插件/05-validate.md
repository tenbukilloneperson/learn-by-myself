# 					validate

```不选
百秀第七天   login_validate页面
```



```javascript
  // 使用以下方式用于设置自定义匹配规则
  //    - 参数1: 规则名称
  //    - 参数2: 规则的检测方式,函数
  //      - 形参1: 当前表单元素内容
  //      - 形参2: 当前表单元素,DOM对象
  //      - 形参3: 设置规则时,给定的属性值(自定义规则时,通常不使用这个参数)
  //    - 参数3: 提示信息
  $.validator.addMethod('psw', function (value, element, params) {
    // 这个函数需要返回布尔类型值,用于决定匹配成功还是失败

    // this.optional(element) 用于检测当前元素是否为必选元素:
    //    - 如果元素为必选:
    //      - 结果恒为false,在逻辑或中,就必须通过后面的检测条件,结果才能为true
    //    - 如果元素为可选:
    //      - 如果没有内容,方法返回一个字符串'dependency-mismatch',转换布尔类型为true,可以避免进行后续检测
    //      - 如果具有内容,结果为false,也只有通过后续检测,结果才能为true

    return this.optional(element) || /^[a-zA-Z0-9]{6,10}$/.test(value);

  }, '不符合密码规则~~~');


  // validate是一款常用的,用于进行表单验证的jQuery插件
  //  - 以下内容是对常用的参数进行说明,完整使用方式可以见以下链接:
  //    - https://www.runoob.com/jquery/jquery-plugin-validate.html
  //    - https://jqueryvalidation.org/documentation/ 官网地址
  $form.validate({
    rules : {
      // 通过表单元素的name属性,作为规则的指定标识
      email_name : {
        required : true, // 当前元素是否必选
        maxlength : 20,
        minlength : 6,
        email : true // 匹配规则为邮箱验证方式
      },
      password : {
        required : true,
        // 设置密码框时,需要自己定义检测规则
        psw : true
      }
    },
    messages : {
      email_name : {
        required : '必须甜,不甜不行!!!~~~'
      },
      password : {
        required : '需要填写密码',
        psw : '密码格式不对'
      }
    },
    submitHandler : function () {
      console.log('呵呵呵呵呵,就不提交~~~');
    }
  });
```

