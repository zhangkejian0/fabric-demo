<template>
  <div class="hello">
    <canvas id="canvas" width="350" height="200"></canvas>
  </div>
</template>

<script>
import { fabric } from 'fabric'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  mounted(){
    console.log(process.env)
    const card = new fabric.Canvas('canvas');
    card.setWidth(350)
    card.setHeight(200)

    card.on('object:modified', (e) => {
        console.log(e.target) // e.target为当前编辑的Object
        // ...旋转，缩放，移动等编辑图层的操作都监听到
        // 所以如果有撤销/恢复的场景，这里可以保存编辑状态
    });

    var rect = new fabric.Rect({

        left:100,//距离画布左侧的距离，单位是像素

        top:100,//距离画布上边的距离

        fill:'red',//填充的颜色

        width:30,//方形的宽度

        height:30//方形的高度

    });
    card.add(rect);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#canvas{
  background: #ccc;
}
</style>
