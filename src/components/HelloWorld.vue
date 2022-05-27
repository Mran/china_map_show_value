<script setup lang="ts">
import {getCurrentInstance, onMounted, ref} from 'vue'
import china from '../../node_modules/echarts/map/json/china.json'
import * as echarts from 'echarts';

onMounted(() => {
  initChart()
})
// 基础配置一下Echarts
const initChart = () => {
  console.log(document.getElementById('mycharts'))
  const myChart = echarts.init(document.getElementById('mycharts'));

  echarts.registerMap('CN', china);
  myChart.setOption(
      {
        layoutSize:'100%',//大小
        title: {},
        tooltip: {
          trigger: 'item',
          formatter: '{b}<br/>{c} (p / km2)'
        },
        toolbox: {
          show: true,
          orient: 'vertical',
          left: 'right',
          top: 'center',
          feature: {
            dataView: {readOnly: false},
            restore: {},
            saveAsImage: {}
          }
        },
        visualMap: {
          min: 0,
          max: 203,
          text: ['最多', '最少'],
          realtime: false,
          calculable: true,
          inRange: {
            color: ['lightskyblue', 'yellow', 'orangered']
          }
        },
        label: {
          normal: {
            textStyle: {
              fontSize: 15,
              fontWeight: 'bold',
              color: 'red'
            }
          }
        },
        series: [
          {
            name: '中国',
            type: 'map',
            map: 'CN',
            label: {
              show: true
            },
            data: [
              {name: "新疆", value: 0},
              {name: "西藏", value: 0},
              {name: "青海", value: 0},
              {name: "四川", value: 18},
              {name: "云南", value: 9},
              {name: "甘肃", value: 1},
              {name: "宁夏", value: 0},
              {name: "内蒙古", value: 3},
              {name: "陕西", value: 3},
              {name: "重庆", value: 5},
              {name: "贵州", value: 6},
              {name: "广西", value: 1},
              {name: "海南", value: 14},
              {name: "广东", value: 89},
              {name: "香港", value: 0},
              {name: "澳门", value: 0},
              {name: "湖南", value: 17},
              {name: "江西", value: 1},
              {name: "福建", value: 24},
              {name: "台湾", value: 0},
              {name: "浙江", value: 55},
              {name: "湖北", value: 6},
              {name: "上海", value: 19},
              {name: "江苏", value: 32},
              {name: "安徽", value: 6},
              {name: "河南", value: 9},
              {name: "河北", value: 13},
              {name: "山东", value: 10},
              {name: "山西", value: 0},
              {name: "北京", value: 203},
              {name: "天津", value: 4},
              {name: "辽宁", value: 4},
              {name: "吉林", value: 5},
              {name: "黑龙江", value: 3},
            ],
            // 自定义名称映射
            nameMap: {}
          }
        ]
      }
  );
  console.log(myChart);
}


</script>

<template>

  <div class="wrapper">

    <div class="mycharts" id="mycharts" ref="mycharts" style="width: 1000px; height: 1000px;"></div>
  </div>
</template>

<style scoped>
a {
  color: #42b983;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}
</style>
