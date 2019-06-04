<template>
  <div>
    <h2>{{ msg }}</h2>
    <div id="c1"></div>
  </div>
</template>

<script>
// 这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
// 例如：import 《组件名称》 from '《组件路径》';
export default {
  name: "g2Demo",
  components: {},
  // 生命周期 - 创建完成（可以访问当前this实例）
  created() {},
  // 生命周期 - 载入后, Vue 实例挂载到实际的 DOM 操作完成，一般在该过程进行 Ajax 交互
  mounted() {
    this.initComponent();
  },
  data() {
    return {
      msg: "",
      chart: null,
      data: [
        { genre: "Sports", sold: 275 },
        { genre: "Strategy", sold: 115 },
        { genre: "Action", sold: 120 },
        { genre: "Shooter", sold: 350 },
        { genre: "Other", sold: 150 }
      ]
    };
  },
  // 方法集合
  methods: {
    initComponent() {
      // 此函数为个人习惯,喜欢创建一个初始化的函数
      this.msg = "vue-cli案例";
      const chart = new G2.Chart({
        container: "c1",
        width: 600,
        height: 300
      })
      chart.source(this.data);
      chart
        .interval()
        .position("genre*sold")
        .color("genre");
      this.chart = chart
      this.chart.render()
    }
  },
  // 计算属性
  computed: {}
}
</script>