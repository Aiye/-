<template>
  <div class="user">
    <div style="position: fixed;bottom: 15px;left: 20px;right: 20px;">
      <van-button style="width:100%;" type="primary" @click="pushEquipment">开始配装</van-button>
    </div>
  </div>
</template> 

<script>
export default {
  data() {
    return {
      type: "",
      list: []
    };
  },
  created() {
    console.log(this.$route.query);
    this.query = this.$route.query;
    this.type = this.query.type;
  },
  mounted() {},
  methods: {
    pushEquipment() {
      this.$router.push({ path: "/equipment", query: this.query });
    }
  }
};
</script>


<style lang="less" scoped>
.user {
}
</style>
