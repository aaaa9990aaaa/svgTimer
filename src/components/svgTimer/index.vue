<template>
  <svg>
    <defs>
      <linearGradient id="linear" x1="0%" y1="0%" x2="0%" y2="100%">
        <stop offset="0%" stop-color="#20FF64" />
        <stop offset="100%" stop-color="#60BAFD" />
      </linearGradient>
    </defs>
    <path :d="getD" 
      stroke="#6d7790a8" 
      fill="none" 
      stroke-width="20" 
      v-bind:style="{'stroke-dasharray':getPerimeter}" >
    </path>
    <path :d="getD" 
      stroke="url(#linear)" 
      fill="none" 
      stroke-width="20" 
      v-bind:style="{'stroke-dasharray':getPerimeter2}"
     >
    </path>
    <circle :cx="getx" :cy="gety" :r="getr" fill="#647080b4"></circle>
    <circle :cx="getx" :cy="gety" :r="getr2" stroke="#20FF64" stroke-width="2" fill="none"></circle>
    <line :x1="linex1" :x2="linex2" :y1="liney1" :y2="liney2" stroke="#20ff64" />
  </svg>
</template>

<script>
export default {
  props: {
    options: {}
  },
  data() {
    return {
      x: 20,
      total: 1,
      num: 0
    }
  },
  watch: {
    //监听num变化
    options: {
　　　　handler(newValue, oldValue) {
　　　　　　this.num = newValue.num
　　　　},
　　　　deep: true
　　}
  },
  mounted() {
    if(this.options.num && this.options.total) {
      this.num = this.options.num
      this.total = this.options.total
    }
    this.getStrokeDasharray()
  },
  computed: {
    //计算外圈
    getD(){
      return "M "+ 1.5*this.x+" "+(this.x*3.5*2-this.x)+" A "+this.x*3.5+" "+this.x*3.5+" 0 1 1 "+(this.x*3.5*2+(this.x/2))+" "+(this.x*3.5*2-this.x)
    },
    //计算百分比长度
    getPerimeter() {
      //计算周长
      let perimeter = this.x*3.5*2*2.102
      return perimeter + " " +perimeter
    },
    //计算百分比长度
    getPerimeter2() {
      //计算周长
      let perimeter = this.x*3.5*2*2.102
      if(this.total) {
        return parseInt(perimeter*this.num/this.total) + " " +perimeter
      }else {
        return "0 "+perimeter;
      }
    },
    //计算中间圆的x坐标
    getx(){
      return this.x*3.5+this.x
    },
    //计算中间圆的y坐标
    gety() {
      return this.x*3.5*1.2
    },
    //计算中间圆的半径
    getr() {
      return this.x*3.5-(this.x/2)-1
    },
    getr2(){
      return this.x
    },
    //获取直线的两个坐标
    linex1(){
      let x = this.getx + this.getr * Math.cos((150+240*this.num/this.total)*Math.PI/180)
      return x;
    },
    liney1(){
      let y = this.gety + this.getr * Math.sin((150+240*this.num/this.total)*Math.PI/180)
      return y;
    },
    linex2() {
      let x = this.getx + this.getr2 * Math.cos((150+240*this.num/this.total)*Math.PI/180)
      return x;
    },
    liney2() {
      let y = this.gety + this.getr2 * Math.sin((150+240*this.num/this.total)*Math.PI/180)
      return y;
    }
  },
  methods: {
    //计算图形的大小
    getStrokeDasharray() {
      //获取图像的宽度
      let width = this.$el.parentNode.offsetWidth; 
      this.x = parseInt(width * 20/180);
    }
  }
}
</script>

<style scoped lang="scss">
  svg {
    width: 100%;
    height: 100%;
    path {
      stroke-dashoffset: 0px;
      transition: stroke-dasharray 1s ease 0s, stroke 1s ease 0s;
    }
  }
</style>