<template>
  <div class="login_container">
    <div class="login_box">
      <div class="avatar_box">
        <img src="../assets/images/avatar.jpg">
      </div>
        <!--   与Login_form数据项绑定   -->
        <!--   设置验证规则:login_form_rules     -->
        <!--   设置引用对象:login_form_ref   -->
        <el-form :model="Login_form" :rules="login_form_rules" ref="login_form_ref" label-width="0px" class="login_form">
          <!--      使用username验证规则    -->
          <el-form-item prop="username">
            <!--    v-model="Login_form.password":与Login_form.username绑定       -->
            <!--    prefix-icon="el-icon-user":显示小图标        -->
            <!--    输入账号        -->
            <el-input v-model="Login_form.username" prefix-icon="el-icon-user"></el-input>
          </el-form-item>
          <!--      使用password验证规则    -->
          <el-form-item prop="password">
            <!--    v-model="Login_form.password":与Login_form.password绑定       -->
            <!--    prefix-icon="el-icon-key":显示小图标        -->
            <!--    show-password:可选是否显示密码        -->
            <!--    输入密码        -->
            <el-input placeholder="" v-model="Login_form.password" show-password prefix-icon="el-icon-key"></el-input>
          </el-form-item>
          <el-form-item>
          <!--      设置重置点击事件:reset_login_form    -->
            <el-button type="danger" class="login_botton" @click="reset_login_form">重置</el-button>
          <!--      设置登录点击事件:login      -->
            <el-button type="success" class="login_botton" @click="login">登录</el-button>
          </el-form-item>
        </el-form>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      // form表单数据项
      Login_form: {
        username: 'zlz',
        password: '123456'
      },
      // form表单验证规则
      login_form_rules: {
        // 用户名输入框验证规则：requied:必填 message:提示信息 trigger;当鼠标移出区域时进行验证
        username: [
          { required: true, message: '请输入用户名', trigger: 'blur' }
        ],
        // 密码输入框验证规则：requied:必填 message:提示信息 trigger;当鼠标移出区域时进行验证
        password: [
          { required: true, message: '请输入密码', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    // 重置点击事件：重置login_form表单
    reset_login_form () {
      this.$refs.login_form_ref.resetFields()
    },
    // 登录点击事件
    login () {
      // 发送登录请求前进行验证，valid保存验证结果
      this.$refs.login_form_ref.validate(valid => {
        // eslint-disable-next-line no-useless-return
        if (!valid) return// 验证不通过，不向服务器发起请求
        // post方式：this.$http().post(参数)
      })
    }
  }
}
</script>
<style lang="less" scoped>
.login_container {
  background-color : #66ccff;
  height:100%;
}

.login_box{
  // 添加背景色 白
  background-color: #ffffff;
  width: 500px;
  height: 309px;
  // 添加 圆角
  border-radius: 3px;
  // 绝对定位
  position: absolute;
  // 居中设置
  left: 50%;
  top: 50%;
  transform: translate(-50%,-50%);
  // 头像样式
  .avatar_box{
    width: 110px;
    height: 110px;
    // 添加圆角
    border-radius: 50%;
    // 添加边框 白
    border: 1px #ffffff;
    // 添加内边距
    padding: 10px;
    // 添加背景色 白
    background-color: #eeeeee;
    // 添加阴影效果 灰
    box-shadow: 0 0 10px #dddddd;
    // 绝对定位
    position: absolute;
    // 水平居中，靠上
    left: 50%;
    transform: translate(-50%,-50%);
    // 头像样式
    img{
      width: 100%;
      height: 100%;
      // 添加圆角
      border-radius: 50%;
    }
  }
}
// 表单区域样式
.login_form{
  // 绝对定位
  position: absolute;
  // 贴底部
  bottom: 0px;
  width: 100%;
  // 设置边距
  padding: 0 20px;
  // border-box 告诉浏览器：你想要设置的边框和内边距的值是包含在width内的
  box-sizing: border-box;
}
// 按钮样式
.login_botton{
  // 靠右浮动
  float: right;
  // 设置外边距
  margin-left: 5px;
}
</style>
