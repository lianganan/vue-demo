<template>
  <el-container class="home">
    <el-header>
      <div class="logo"></div>
      <div class="logout">欢迎使用 <a href="">退出</a></div>
      <div class="title">体顺后台管理系统</div>
    </el-header>
    <el-container>
      <el-aside width="200px">
        <el-menu
          default-active="userList"
          class="el-menu-vertical-demo"
          @open="handleOpen"
          @close="handleClose"
          background-color="#545c64"
          text-color="#fff"
          active-text-color="#ffd04b"
          router>
          <el-submenu index="users">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>用户管理</span>
            </template>
            <el-menu-item index="userList">
              <i class="el-icon-menu"></i>
              <span slot="title">用户列表</span>
            </el-menu-item>
          </el-submenu>
          <el-submenu index="quanxian">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>权限管理</span>
            </template>
            <el-menu-item index="a">
              <i class="el-icon-menu"></i>
              <span slot="title">导航一</span>
            </el-menu-item>
            <el-menu-item index="b">
              <i class="el-icon-menu"></i>
              <span slot="title">导航二</span>
            </el-menu-item>
          </el-submenu>
        </el-menu>
      </el-aside>
      <el-main>
        <router-view />
      </el-main>
    </el-container>
  </el-container>
</template>

<script>
export default {
  data () {
    return {
      activeName: '1'
    }
  },
  methods: {
    handleOpen (key, keyPath) {
      console.log(key, keyPath)
    },
    handleClose (key, keyPath) {
      console.log(key, keyPath)
    }
  }
}
</script>

<style lang="less" scoped>
  .home {
    height: 100%;
    .el-header {
      background-color: #aaa;
      overflow: hidden;
      .logo {
        width: 200px;
        height: 60px;
        background: url('../assets/logo.png') center left no-repeat ;
        background-size: contain;
        float: left;
      }
      .logout {
        width: 200px;
        height: 60px;
        float: right;
        text-align: center;
        line-height: 60px;
      }
      .title {
        height: 60px;
        padding: 0 200px;
        text-align: center;
        line-height: 60px;
        font-size: 20px;
      }
    }
    .el-container {
      .el-aside {
        background-color: rgb(84, 92, 100);
        .el-submenu {
          width: 200px;
        }
      }
      .el-main {
        background-color: #ccc;
      }
    }
  }
</style>
