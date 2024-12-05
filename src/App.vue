<template>
  <div>
    <h1>ECharts 示例</h1>
    <e-chart-component :chartData="chartData1" chartType="bar" />
    <e-chart-component :chartData="chartData2" chartType="line" />
    <e-chart-component :chartData="chartData3" chartType="pie" />
  </div>
</template>

<script>
import EChartComponent from './components/EChartComponent.vue';

export default {
  name: 'App',
  components: {
    EChartComponent,
  },
  data() {
    return {
      chartData1: {
        title: '柱状图示例',
        xAxis: ['苹果', '香蕉', '橙子', '梨', '樱桃'],
        series: {
          name: '销售量',
          data: [5, 20, 36, 10, 10],
        },
      },
      chartData2: {
        title: '折线图示例',
        xAxis: ['一月', '二月', '三月', '四月', '五月'],
        series: {
          name: '用户数',
          data: [150, 200, 300, 250, 400],
        },
      },
      chartData3: {
        title: '饼图示例',
        xAxis: [],
        series: {
          name: '访问来源',
          data: [
            { value: 40, name: '直接访问' },
            { value: 30, name: '邮件营销' },
            { value: 20, name: '联盟广告' },
            { value: 10, name: '视频广告' },
          ],
        },
      },
    };
  },
};
</script>

<style>
/* 可以在这里添加全局样式 */
</style>
