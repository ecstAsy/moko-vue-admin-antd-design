<!--
 * @Author: ecstAsy
 * @Date: 2021-12-09 11:33:00
 * @LastEditTime: 2021-12-09 13:53:04
 * @LastEditors: ecstAsy
-->

<template>
  <a-card>
    <row-title
      title="访问量"
      value="8,846"
      tooltip="访问量"
    />
    <div class="content">
      <div
        ref="chartDom"
        style="width: 90%;height: 46px;"
      />
    </div>
    <a-row class="footer">
      日访问量 1,234
    </a-row>
  </a-card>
</template>

<script setup lang="ts">
import { ref, Ref, onMounted } from "vue";
import * as echarts from "echarts/core";
import { GridComponent } from "echarts/components";
import { LineChart } from "echarts/charts";
import { UniversalTransition } from "echarts/features";
import { CanvasRenderer } from "echarts/renderers";
import RowTitle from "./RowTitle.vue";

echarts.use([GridComponent, LineChart, CanvasRenderer, UniversalTransition]);

const chartDom = ref<Ref | null>(null);
const myChart = ref<any>(null);

const setInit = () => {
  myChart.value = echarts.init(chartDom.value);
  const option = {
    xAxis: {
      type: "category",
      boundaryGap: false,
      show: false,
    },
    yAxis: {
      type: "value",
      show: false,
    },
    series: [
      {
        data: [3, 4, 7, 3, 5, 8, 9, 5, 10, 5],
        type: "line",
        smooth: true,
        areaStyle: {
          color: "#7367F0",
        },
      },
    ],
  };
  if (!option) return;
  myChart.value.setOption(option);
};
onMounted(() => setInit());
</script>
