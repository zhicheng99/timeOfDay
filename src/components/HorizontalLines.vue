<template>
  <div>
    <div v-for="(item, index) in horizontalLines" :key="index">
      <div
        class="horizontalLine"
        v-bind:style="{
          left: item.left + 'px',
          width: item.width + 'px',
          top: (index + 1) * 22 + index * 8 + 'px',
          borderTop:
            'dashed ' + (color[index] ? color[index] : '#ccc') + ' 1px',
        }"
      >
        <HorizontalTip
          v-bind:sec-obj="item"
          v-bind:text-color="color[index] ? color[index] : '#ccc'"
        ></HorizontalTip>
      </div>
    </div>
  </div>
</template>

<script>
import HorizontalTip from "./HorizontalTip.vue";
export default {
  components: {
    HorizontalTip,
  },
  props: ["horizontalLines"],
  data() {
    return {
      // lines: [],
      color: this.$parent._data.color,
    };
  },
  mounted() {
    // console.log(this.$parent._data.color)
  },
  // watch: {
  //   horizontalLines: {
  //     handler: function (v) {
  //       this.lines = v;
  //     },
  //     immediate: true,
  //   },
  // },
};
</script>

<style scoped>
.horizontalLine {
  position: absolute;
  top: 17px;
  height: 0;
  line-height: 0;
  border-top: dashed #333 1px;
}
.horizontalLine:before {
  content: "";
  position: absolute;
  left: 0;
  top: 0;
  display: block;
  width: 8px;
  height: 8px;
  /* background:red; */
  box-sizing: border-box;
  border-left: solid #666 1px;
  border-top: solid #666 1px;
  transform-origin: 0% 0%;
  transform: scale(1, 0.5) rotate(-45deg);
}
.horizontalLine:after {
  content: "";
  position: absolute;
  right: 0;
  top: 0;
  display: block;
  width: 8px;
  height: 8px;
  /* background:red; */
  box-sizing: border-box;
  border-top: solid #666 1px;
  border-right: solid #666 1px;
  transform-origin: 100% 0%;
  transform: scale(1, 0.5) rotate(45deg);
}
</style>