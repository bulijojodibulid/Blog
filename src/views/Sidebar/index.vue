<template>
  <div class="sidebar-container">
    <div class="head">
      <div class="gif"></div>
      <span class="desc"></span>
    </div>
    <div class="body"></div>
    <div class="foot"></div>
  </div>
</template>

<script>
export default {
    name: 'Sidebar'
}
</script>

<style lang="less" scoped>
.sidebar-container{
    width: 300px;
    height: 100vh;
    border: 1px solid red;

    .head{
      width: 100%;
      height: 150px;
      border: 1px solid lawngreen;
      padding-top: 30px;
      text-align: center;
      .gif{
        width: 115px;
        height: 115px;
        border: 3px solid rgb(165, 166, 255);
        border-radius: 50%;
        margin: auto;
        background-position: -173px -46px;
        background-repeat: no-repeat;
        background-image: url('~@/assets/gif/lookForward.gif');
      }
    }
}
</style>