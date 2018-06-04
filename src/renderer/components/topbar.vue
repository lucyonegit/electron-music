<template>
  <div>
    <div class="topbar">
      <div class="logo"><img src="../assets/header/logo.png" alt=""></div>
      <div class="search">
        <input type="text" id="search_inp" placeholder="请输入想听的歌...">
      </div>
      <div class="meau">
        <span @click="minwin"><Icon class="min" type="ios-minus-outline" size="22" color="#999999" title="最小化"></Icon></span>
        <span  @click="modal=true"><Icon class="close" type="ios-close-outline" size="22" color="#999999" title="关闭" ></Icon></span>
      </div>
    </div>
    <Modal
        title="退出"
        width="25"
        v-model="modal"
        @on-ok="close('close')"
        :styles="{top: '20px'}"
        class-name="vertical-center-modal">
        <p>确认退出吗？</p>
    </Modal>
  </div>
</template>
<script>
const {ipcRenderer: ipc} = require('electron');
export default {
  name:"topbar",
  data(){
    return{
      modal: false,
    }
  },
  methods:{
   close:function(e){
     ipc.send(e);
   },
   minwin:function(){
      ipc.send("min");
   }
  }
}
</script>
<style>
  .vertical-center-modal{
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 100px;
    }
  .ivu-modal{
        top: 0;
    }
  .topbar{
    width: 100%;
    height: 45px;
    background-color: rgb(67,72,88);
    box-shadow: -1px -1px 12px 1px rgb(160,160,160);
    -webkit-app-region: drag;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
  }
  .logo{
    margin-left: 20px;
  }
  .logo img{
    width:35px;
    height:35px;
  }
  .search{
    -webkit-app-region: no-drag;
  }
  #search_inp{ 
    width: 250px;
    height: 28px;
    border: 1px solid rgb(180,180,180);
    background-color: rgb(230,230,230);
    outline: none;
    border-radius: 20px;
    padding-left: 10px;
    color:rgb(110,110,110)
  }
  #search_inp::-webkit-input-placeholder{
    font-size: 12px;
    font-family: "微软雅黑";
}
.meau{
  margin-right: 20px;
  cursor: pointer;
  -webkit-app-region:no-drag;
}
.min{
  margin-right:10px;
  -webkit-app-region:no-drag;
  transition:all .2s ease;
}
.min:hover{
  color:#111111 !important;
}
.close{
  -webkit-app-region:no-drag;
  transition:all .2s ease;
}
.close:hover{
  color:#990000 !important;
}
.ivu-modal-footer button+button {
    background-color: rgb(40,42,44);
    border-radius: 30px;
}
</style>