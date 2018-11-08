<template>
  <div class="login">
    <el-form :model="form" ref="form" status-icon :rules="rules"  label-width="80px">
      <img src="../assets/logo.png" alt="">
      <el-form-item label="用户名" prop="username">
        <el-input v-model="form.username"></el-input>
      </el-form-item>
      <el-form-item label="密码" prop="password">
        <el-input v-model="form.password" type="password"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="submitForm">登录</el-button>
        <el-button  @click="resetForm">重置</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      form: {
        username: '',
        password: ''
      },
      rules: {
        username: [
          { required: true, message: '请输入用户名', trigger: 'blur' },
          { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
        ],
        password: [
          { required: true, message: '请输入密码', trigger: 'blur' },
          { min: 6, max: 12, message: '长度在 6 到 12 个字符', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    resetForm () {
      this.$refs.form.resetFields()
    },
    submitForm () {
      this.$refs.form.validate(valid => {
        if (valid) {
          axios.post('http://localhost:8888/api/private/v1/login', this.form)
            .then(res => {
              console.log(res.data)
              if (res.data.meta.status === 200) {
                this.$message.success('登录成功')
                this.$router.push({path: '/home'})
              } else {
                this.$message.error('用户名或密码错误')
              }
            })
        } else {
          this.$message.error('用户名或密码错误')
          return false
        }
      })
    }
  }
}
</script>

<style lang="less">
.login {
  height: 100%;
  background-color: #499cff;
  overflow: hidden;
  .el-form {
    width: 400px;
    background-color: #fff;
    margin: 200px auto 0;
    padding: 75px 20px 15px;
    border-radius: 20px;
    position: relative;
    img {
      width: 100px;
      height: 100px;
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      top: -60px;
      background-color: #fff;
      border-radius: 50%;
      border: 10px solid #fff;
    }
    .el-button+.el-button {
      margin-left: 50px;
    }
  }

}
#app {
  height: 100%;
}
</style>
