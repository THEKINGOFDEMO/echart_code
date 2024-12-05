<template>
    <div ref="chartRef" :style="{ width: '100%', height: '400px' }"></div>
  </template>
  
  <script>
  import { ref, onMounted, onBeforeUnmount } from 'vue';
  import * as echarts from 'echarts';
  
  export default {
    name: 'EChartComponent',
    props: {
      chartData: {
        type: Object,
        required: true,
      },
      chartType: {
        type: String,
        default: 'bar',
      },
    },
    setup(props) {
      const chartRef = ref(null);
  
      const initChart = () => {
        const chartInstance = echarts.init(chartRef.value);
  
        const options = {
          title: {
            text: props.chartData.title,
          },
          tooltip: {},
          xAxis: {
            data: props.chartData.xAxis,
          },
          yAxis: {},
          series: [
            {
              name: props.chartData.series.name,
              type: props.chartType,
              data: props.chartData.series.data,
            },
          ],
        };
  
        // 特殊处理饼图的配置
        if (props.chartType === 'pie') {
          options.series[0].data = props.chartData.series.data;
          options.series[0].label = {
            formatter: '{b}: {c} ({d}%)',
          };
          options.series[0].radius = '50%';
        }
  
        chartInstance.setOption(options);
      };
  
      onMounted(() => {
        initChart();
        window.addEventListener('resize', initChart);
      });
  
      onBeforeUnmount(() => {
        window.removeEventListener('resize', initChart);
      });
  
      return {
        chartRef,
      };
    },
  };
  </script>
  
  <style scoped>
  /* 可以在这里添加样式 */
  </style>
  