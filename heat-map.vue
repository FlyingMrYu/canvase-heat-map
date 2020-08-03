<template>
  <div ref="mapCan" class="heat-map-content">
    <div id="heat"></div>
  </div>
</template>

<script>
import bg from "@/assets/img/home/bg.png";
import "./js/heat";
export default {
  name: "heat-map-content",
  data() {
    return {};
  },
  methods: {
    initMaps(width, height) {
      var setting = {
        width: width,
        height: height,
        imgurl: bg,
        points: [
            {
              x: 100, // 坐标x,
              y: 100, // 坐标y
              ratio: 25, // 最小半径
              opacity: 0.9, // 最大透明度
            },
             {
              x: 101, // 坐标x,
              y: 81, // 坐标y
              ratio: 25, // 最小半径
              opacity: 0.9, // 最大透明度
            },
        ],
      };
      // 随机数据
      // for (var i = 0; i < 300; i++) {
      //   setting.points[i] = {
      //     x:
      //       setting.width / 5 +
      //       Math.random() * (setting.width - (setting.width / 5) * 2), // 坐标x,
      //     y:
      //       setting.height / 5 +
      //       Math.random() * (setting.height - (setting.height / 5) * 2), // 坐标y
      //     ratio: 30 + Math.random(), // 半径
      //     opacity: 0.9,
      //   };
      // }

      // 不带setting 则使用随机假数据
      heat("#heat").load(setting);
      // 设置宽度
    //   heat("canvas", heat("#heat")).css("width: 100%");
    },
    // 获取地图宽高
    getMapSize() {
        console.log(1840 / 1020,'1840 / 1020');
      let width = this.$refs.mapCan.offsetWidth;
      let height = (width/(1840 / 1020)).toFixed(2);
      Promise.all([width, height]).then((result) => {
        console.log(width/ height, height,"height");
        this.initMaps(...result);
      });
    },
  },
  mounted() {
    this.getMapSize();
  },
};
</script>

<style scoped lang="scss">
.heat-map-content {
  width: 100%;
  height: 100%;
}
</style>
