<template>
<svg ref="movingSquareArea" width="256" height="256">
  <rect @click="changeMyColor()" :x="x" :y="y" :width="rect" :height="rect" :stroke="stroke" :stroke-width="width" :fill="color" />
</svg>

</template>
<script>
export default {
  props:['color','stroke'],
methods: {
    changeMyColor() {
        this.color = 'pink';
    },
},
  mounted() {
      let targetX = 0;
    let targetY = 0;
      this.$refs.movingSquareArea.addEventListener('click',(event)=>{
       targetX = event.clientX;
       targetY = event.clientY;
      });
      window.setInterval(()=>{
          if(this.x>targetX) {
            this.x-=1* Math.random();

          } else if (this.x<targetX) {
              this.x+=1* Math.random();
          }
           if(this.y>targetY) {
            this.y-=1* Math.random();

          } else if (this.y<targetY) {
              this.y+=1* Math.random();
          }
        //  const time = new Date().getTime()*0.005;
        //this.x =Math.cos(time)*50 +100;
        //this.y = Math.sin(time)*50 +100;
      },10);
  },
  data() {
    return {
        width: 1,
        x: 80,
        y: 140,
        rect: 15,
    };
  },
};
</script>
