<template>
  <div id="app">
    <TimeOfDay
      v-bind:start-time="startTime"
      v-bind:allow-update="true"
      v-bind:end-time="endTime"
      v-bind:time-part.sync="section"
    ></TimeOfDay>
  </div>
</template>

<script>
import TimeOfDay from "./components/TimeOfDay.vue";

export default {
  name: "App",
  data() {
    return {
      startTime: "2021/02/03 10:00",
      endTime: "2021/02/03 19:00",

      //每一组生成一个时间轴
      section: [
        ["2021/02/03 10:00", "2021/02/03 12:00"],
        ["2021/02/03 11:00", "2021/02/03 12:35"],
        ["2021/02/03 12:23", "2021/02/03 16:44"],
        ["2021/02/03 10:33", "2021/02/03 18:35"],
        ["2021/02/03 11:22", "2021/02/03 16:55"], 
      ],
    };
  },
  methods: {
    fun: function () {
      console.log(this.section);
    },
  },
  components: {
    TimeOfDay,
  },
  watch: {
    section: {
      handler: function (v) {
        console.log(v);
      },
      deep: true,
    },
  },
};
</script>

<style>
#app {
}
</style>
