<template>
  <div id="app">
    <Topbar></Topbar>
    <Main></Main>
    <router-view></router-view>
  </div>
</template>

<script>

import Topbar from "./components/topbar";
import Main from "./components/content"
  export default {
    name: 'music',
    components:{Topbar,Main}
  }
</script>
<style>
  html,body{
    width: 100%;
    margin: 0;
    padding: 0;
    font-family: "微软雅黑";
    background-color: rgb(220,220,220);
  }
</style>
