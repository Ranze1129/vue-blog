<template>
  <div class="notFound">
    <div class="content">
      <div>当前页面不存在，请检查网址是否正确</div>
      <div>
        返回
        <router-link to="/">首页</router-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NotFound'
};
</script>

<style scoped lang="less">
.notFound {
  display: flex;
  justify-content: center;
  padding-top: 60px;
  > .content {

  }
}
a {
  color: #149739FF;
}

</style>