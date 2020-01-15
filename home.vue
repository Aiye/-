<template>
  <div class="home">
    <van-grid :column-num="2">
      <van-grid-item v-for="(item,index) in list" :key="index" @click="pushUser(item)">
        <img slot="icon" style="width: 100%;" :src="item.img" />
        <div slot="text" style="font-size:20px;font-weight: 500;">{{item.name}}</div>
      </van-grid-item>
    </van-grid>
  </div>
</template>

<script>
export default {
  name: "home",
  data() {
    return {
      query: null,
      list: [
        {
          name: "天罡",
          img: "http://i3.gbimg.cn/zt/2019/06/26/pmain/images/tg_rw_img.png",
          type: "tg"
        },
        {
          name: "斩风",
          img: "http://i3.gbimg.cn/zt/2019/06/26/pmain/images/zf_rw_img.png",
          type: "zf"
        },
        {
          name: "御剑",
          img: "http://i3.gbimg.cn/zt/2019/06/26/pmain/images/yj_rw_img.png",
          type: "yj"
        },
        {
          name: "咒隐",
          img: "http://i3.gbimg.cn/zt/2019/06/26/pmain/images/zy_rw_img.png",
          type: "zy"
        },
        {
          name: "珑瑛",
          img: "http://i3.gbimg.cn/zt/2019/06/26/pmain/images/ly_rw_img.png",
          type: "ly"
        },
        {
          name: "异芳",
          img: "http://i3.gbimg.cn/zt/2019/06/26/pmain/images/yf_rw_img.png",
          type: "yf"
        },
        {
          name: "司命",
          img: "http://i3.gbimg.cn/zt/2019/06/26/pmain/images/sm_rw_img.png",
          type: "sm"
        },
        {
          name: "妙法",
          img: "http://i3.gbimg.cn/zt/2019/06/26/pmain/images/mf_rw_img.png",
          type: "mf"
        }
      ]
    };
  },
  mounted() {
    console.log(this.$route.query);
    this.query = this.$route.query;
    this.type = this.query.type;
  },
  methods: {
    pushUser() {
      this.$router.push({ path: "/equipment", query: this.query });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
