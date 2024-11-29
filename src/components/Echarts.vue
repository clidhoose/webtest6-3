<template>
    <div class="chart-container">
      <div ref="chart1" class="chart"></div>
      <div ref="chart2" class="chart" style="margin-top: 20px;"></div>
    </div>
  </template>
  
  <script>
  import * as echarts from 'echarts';
  
  export default {
    name: 'EchartsComponent',
    data() {
      return {
        chart1: null,
        chart2: null,
        todos: [
          { text: '任务1' },
          { text: '任务2' },
          { text: '任务3' }
        ]
      };
    },
    mounted() {
      this.chart1 = echarts.init(this.$refs.chart1);
      const option1 = {
        tooltip: {},
        xAxis: {
          data: this.todos.map(todo => todo.text)
        },
        yAxis: {},
        series: [{
          name: '数量',
          type: 'bar',
          data: this.todos.map(() => 1)
        }]
      };
      this.chart1.setOption(option1);
  
      this.chart2 = echarts.init(this.$refs.chart2);
      const option2 = {
       
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'cross',
            label: {
              backgroundColor: '#6a7985'
            }
          }
        },
        legend: {
          data: ['Email', 'Union Ads', 'Video Ads', 'Direct', 'Search Engine']
        },
        toolbox: {
          feature: {
            saveAsImage: {}
          }
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '3%',
          containLabel: true
        },
        xAxis: [
          {
            type: 'category',
            boundaryGap: false,
            data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
          }
        ],
        yAxis: [
          {
            type: 'value'
          }
        ],
        series: [
          {
            name: 'Email',
            type: 'line',
            stack: 'Total',
            areaStyle: {},
            emphasis: {
              focus: 'series'
            },
            data: [120, 132, 101, 134, 90, 230, 210]
          },
          {
            name: 'Union Ads',
            type: 'line',
            stack: 'Total',
            areaStyle: {},
            emphasis: {
              focus: 'series'
            },
            data: [220, 182, 191, 234, 290, 330, 310]
          },
          {
            name: 'Video Ads',
            type: 'line',
            stack: 'Total',
            areaStyle: {},
            emphasis: {
              focus: 'series'
            },
            data: [150, 232, 201, 154, 190, 330, 410]
          },
          {
            name: 'Direct',
            type: 'line',
            stack: 'Total',
            areaStyle: {},
            emphasis: {
              focus: 'series'
            },
            data: [320, 332, 301, 334, 390, 330, 320]
          },
          {
            name: 'Search Engine',
            type: 'line',
            stack: 'Total',
            label: {
              show: true,
              position: 'top'
            },
            areaStyle: {},
            emphasis: {
              focus: 'series'
            },
            data: [820, 932, 901, 934, 1290, 1330, 1320]
          }
        ]
      };
      this.chart2.setOption(option2);
    },
    beforeUnmount() {
      if (this.chart1) {
        this.chart1.dispose();
      }
      if (this.chart2) {
        this.chart2.dispose();
      }
    }
  };
  </script>
  
  <style scoped>
  .chart-container {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  .chart {
    width: 600px;
    height: 400px;
  }
  </style>