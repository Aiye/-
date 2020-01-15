<template>
  <div class="equipment">
    <div style="position: fixed;z-index: 999;width: 100%;">
      <van-dropdown-menu>
        <van-dropdown-item
          v-model="profession"
          :options="professionOption"
          @change="professionChange"
        />
        <van-dropdown-item
          v-model="equipmentLevel"
          :options="equipmentLevelOption"
          @change="equipmentLevelChange"
        />
      </van-dropdown-menu>
    </div>
    <div style="height:50px;"></div>
    <div>
      <div
        class="cell van-hairline--bottom"
        v-for="(item,index) in list"
        :key="index"
        @click="showImg(index)"
      >
        <img class="img" :src="item.img" alt />
        <div style="padding-top:10px;">{{item.name}}</div>
      </div>
    </div>
  </div>
</template>

<script>
import equipmentJson from "../js/equipment.json";
import { ImagePreview } from "vant";

export default {
  comments: { ImagePreview },
  data() {
    return {
      type: "",
      list: [],
      profession: "",
      professionOption: [
        { text: "天罡", value: "tg" },
        { text: "斩风", value: "zf" },
        { text: "御剑", value: "yj" },
        { text: "咒隐", value: "zy" },
        { text: "珑瑛", value: "ly" },
        { text: "异芳", value: "yf" },
        { text: "司命", value: "sm" },
        { text: "妙法", value: "mf" }
      ],
      equipmentLevel: "235",
      equipmentLevelOption: [
        { text: "235", value: "235" },
        { text: "240", value: "240" },
        { text: "255", value: "255" }
      ]
    };
  },
  created() {
    let query = this.$route.query;
    this.profession = query.type;
    this.getData();
  },
  mounted() {},
  methods: {
    getData() {
      let data = equipmentJson[this.profession] || {};
      let list = data[this.equipmentLevel] || [];
      this.list = list;
      console.log(this.list);
    },
    showImg(index) {
      let images = [];
      this.list.forEach(element => {
        images.push(element.img);
      });
      ImagePreview({
        images: images,
        startPosition: index
      });
    },
    professionChange(value) {
      console.log(value);
      this.profession = value;
      this.getData();
    },
    equipmentLevelChange(value) {
      this.equipmentLevel = value;
      this.getData();
    }
  }
};
</script>

<style lang="less" scoped>
.equipment {
  .cell {
    display: inline-block;
    width: 50%;
    padding: 20px 0;
    text-align: center;
    .img {
      width: 90%;
      vertical-align: top;
    }
  }
}
</style>
