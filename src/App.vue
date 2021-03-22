<template>
  <div id="app">
    <quick-menu class="quick-menu" :menu-count="count" :icon-class="icons" :menu-url-list="list" @process="handProcess"></quick-menu>
    <canvas id="canvas" ref="canvas" width="100%" height="100%"></canvas>
  </div>
</template>

<script>
import { fabric } from 'fabric'
import quickMenu from 'vue-quick-menu'
export default {
  name: "App",
  components: {
    quickMenu
  },
  data(){
    return {
      card: null,
      count: 3,
      icons:["iconfont icon-xianduan","iconfont icon-tx-tuoyuanxing","iconfont icon-tx-zhengfangxing"],
      list:[{'isLink':false},{'isLink':false},{'isLink':false}],
    }
  },
  methods:{
    handProcess(e){
      console.log(e)
    },
    initCanvas(){
      this.card = new fabric.Canvas('canvas',{
         backgroundColor: '#fff',
      });
      this.card.setWidth(1000)
      this.card.setHeight(500);
      this.card.on('mouse:down', (e) => {
        console.log(e)
      })
      this.card.on('mouse:up', (e) => {
        console.log(e)
      })
      // this.card.on('mouse:move', (e) => {
      //   console.log(e)
      // })
    }
  },
  mounted(){
    this.initCanvas();
  }
};
</script>

<style lang="less">
*{
  margin: 0;
  padding: 0;
}
html,body{
  width: 100%;
  height: 100%;
}
#app {
  background-image: url('./assets/Explosion_4k.jpg');
  width: 100%;
  height: 100%;
}
.canvas-container{
  display: flex;
  justify-content: center;
  align-items: center;
}
#canvas{
  width: 100%;
  height: 100%;
}
.sub-menu{
  a{
    display: flex !important;
    justify-content: center;
    align-items: center;
    i{
      margin-top: 0 !important;
    }
  }
}
.quick-menu{
  position: fixed;
  z-index: 100;
}
</style>
