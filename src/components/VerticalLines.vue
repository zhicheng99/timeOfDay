<template>
  <div>
    <div v-for="(item, index) in verticalLines" :key="index">
      <!-- 开始线 -->
      <div
        class="verticalLine"
        v-bind:style="{
          left: item[0].left + 'px',
          height: index * 30 + 30 + 'px',
        }"
      >
        <div v-bind:style="{ color: color[index] ? color[index] : '#ccc' }">
          {{ item[0].time | format }}
        </div>
      </div>
      <!-- 结束线 -->
      <div
        class="verticalLine"
        v-bind:style="{
          left: item[1].left + 'px',
          height: index * 30 + 30 + 'px',
        }"
      >
        <div v-bind:style="{ color: color[index] ? color[index] : '#ccc' }">
          {{ item[1].time | format }}
        </div>
      </div>
    </div>
  </div>
</template> 

<script>
export default {
  props: ["verticalLines"],
  data() {
    return {
      // lines: [],
      color: this.$parent._data.color,
    };
  },
  filters: {
    format: function (v) {
      return v.split(" ")[1];
    },
  },
  // watch: {
  //   verticalLines: {
  //     handler: function (v) {
  //       this.lines = v;
  //     },
  //     immediate: true,
  //   },
  // },
};
</script>

<style scoped>
.verticalLine {
  position: absolute;
  top: 2px;
  width: 0;
  height: 30px;
  border-left: dashed #999 1px;
  pointer-events: none;
}
.verticalLine div {
  position: absolute;
  bottom: -12px;
  left: 0;
  white-space: nowrap;
  font-size: 12px;
  transform-origin: 0% 50%;
  transform: rotate(35deg);
  pointer-events: none;
}
</style>