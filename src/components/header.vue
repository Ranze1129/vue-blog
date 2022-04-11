<template>
  <header :class="{login: isLogin, 'no-login': !isLogin}">
    <template v-if="!isLogin">
      <h1 class="titleName"><i class="el-icon-s-unfold"></i> 即刻分享</h1>
      <h1>Let's share </h1>
      <p>分享你的生活</p>
      <div class="btns">
        <router-link to="/login">
          <el-button>立即登录</el-button>
        </router-link>
        <router-link to="/register">
          <el-button>注册账号</el-button>
        </router-link>
      </div>
    </template>
    <template v-if="isLogin">
      <div class="title">
        <i class="el-icon-s-unfold"></i>
        <h1>
          <router-link to="/">
            Let's share
          </router-link>
        </h1>
        <router-link to="/">
          <div class="back">首页</div>
        </router-link>
      </div>
      <router-link to="/create">
        <el-button type="success" icon="el-icon-edit" class="write">写博客</el-button>
      </router-link>
      <div class="user">
        <img class="avatar" :src="user.avatar" :alt="user.username" :title="user.username">
        <ul>
          <li>
            <router-link to="/my">我的</router-link>
          </li>
          <li><a href="#" @click="onLogout">注销</a></li>
        </ul>
      </div>
    </template>
  </header>
</template>

<script>

import auth from '@/api/auth'

window.auth = auth

import {mapGetters, mapActions} from 'vuex'

export default {
  data() {
    return {}
  },
  computed: {
    ...mapGetters([
      'isLogin',
      'user'
    ])
  },
  created() {
    this.checkLogin()
  },

  methods: {
    ...mapActions([
      'checkLogin',
      'logout'
    ]),
    onLogout() {
      this.logout()
    }
  },
}
</script>


<style lang="less">
@import "../assets/base.less";
header.no-login {
  padding: 0 12% 30px 12%;
  background: @bgColor;
  display: grid;
  justify-items: center;
  position: relative;
  .titleName {
    position: absolute;
    padding: 0 16%;
    left: 0;
    top: -52px;
    font-size: 34px;
  }
  h1 {
    color: #fff;
    font-size: 40px;
    margin: 60px 0 0 0;
  }
  p {
    margin: 15px 0 0 0;
    color: #fff;
  }
  .btns {
    margin-top: 20px;
    margin-bottom: 20px;
  }
  button {
    margin: 20px 5px 0;
  }
  .el-button:hover {
    color: @bgColor;
    background-color: #d2fcc8;
  }
}
header.login {
  display: flex;
  align-items: center;
  background: rgb(244, 245, 245);
  box-shadow: 0 0 5px @bgColor;
  .el-icon-s-unfold::before{
    font-size: 38px;
    margin-right: 10px;
    color: @bgColor;
  }
  .write {
    background: @bgColor;
    > span {
      font-size: 16px;
    }
  }
  .title {
    flex: 1;
    display: flex;
    align-items: center;
    flex-wrap: nowrap;
  }
  h1 {
    margin: 0;
    padding: 0;
    font-size: 40px;
    text-transform: uppercase;
    min-width: 264px;

    a {
      color: @bgColor;
    }
  }
  .back {
    font: 18px/1.6 Arial, "Microsoft YaHei", "黑体", "宋体", sans-serif;
    color: #7d7c7c;
    padding: 2px 24px;
    &:hover {
      color: #0aad0a;
    }
  }
  .edit {
    color: #fff;
    font-size: 30px;
  }
  .avatar {
    width: 40px;
    height: 40px;
    border: 1px solid @themeColor;
    border-radius: 50%;
    margin-left: 30px;
  }
  .user {
    position: relative;
    top: 4px;
    ul {
      display: none;
      position: absolute;
      right: 0;
      list-style: none;
      border: 1px solid #eaeaea;
      margin: 0;
      padding: 0;
      background-color: #fff;
      a {
        text-decoration: none;
        color: #333;
        font-size: 12px;
        display: block;
        padding: 5px 10px;
        &:hover {
          background-color: #eaeaea;
        }
      }

    }

    &:hover ul {
      display: block;
    }
  }
}


</style>
