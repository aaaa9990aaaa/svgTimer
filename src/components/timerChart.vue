<template>
  <div class="chart">
    <div class="chart_content">
      <svg-timer :options="options" />
    </div>
    <div class="chart_in">
      <span class="chart_begin">0</span>
      <span class="chart_num">{{options.num}}</span>
      <span class="chart_end">{{options.total}}</span>
      <span class="chart_lable">{{options.company}}</span>
      <span class="chart_in_data">{{getPercentage()}}</span>
      <span>完成度</span>
    </div>
  </div>
</template>

<script>
import svgTimer from "@/components/svgTimer"
export default {
  components: {
    svgTimer
  },
  props: {
    options:{}
  },
  methods: {
    getPercentage() {
      let point = this.options.num/this.options.total;
      return parseInt(point*100)+"%";
    }
  }
}
</script>

<style scoped lang="scss">
  .chart{
    width: 15rem;
    height: 15rem;
    position: relative;
    .chart_content {
      width: 15rem;
      height: 15rem;
      margin: 0 auto;
    }
    .chart_in {
      position: absolute;
      width: 100%;
      height: 100%;
      left: -0.1rem;
      top: 0;
      text-align: center;
      color: #fff;
      .chart_begin {
        position:absolute;
        left: 24%;
        top: 52%;
        font-family: 'DIGITAL-Regular';
      }
      .chart_end {
        position: absolute;
        right: 24%;
        top: 52%;
        font-family: 'DIGITAL-Regular';
      }
      .chart_num {
        position: absolute;
        font-size: 1.8rem;
        font-family: 'DIGITAL-Regular';
        line-height: 2rem;
        top: calc(50% - 1.6rem);
        width: 100%;
        text-align: center;
      }
      .chart_lable {
        font-size: 1.3rem;
        margin-top: 8.5rem;
      }
      .chart_in_data {
        margin-top: 1rem;
        color: #3AFE76;
      }
      span {
        font-size: 1.5rem;
        display: block;
      }
    }
  }
</style>