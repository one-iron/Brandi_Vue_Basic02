
<template>
  <div class="end">
    <div class="bannerBox" v-for="banner in banners" v-bind:key="banner.id">
      <div
        class="imgBox"
        :style="`backgroundImage: url(${banner.image_url}); backgroundSize: cover`"
      ></div>
      <EndSlot>
        <div slot="end-header"> 안녕하십니까 고객님</div>
        <div slot="end-container"> {{banner.id}} 기획전은 이미 종료되었습니다.</div>
        <div slot="end-footer"> 찾아주셔서 감사합니다. </div>
      </EndSlot>
    </div>
  </div>
</template>



<script>
import axios from "axios";
import EndSlot from "./endSlot";

export default {
  data() {
    return {
      banners: []
    };
  },

  created: async function getBanners() {
    try {
      const res = await axios.get("/static/endBannersImg.json");
      this.banners = res.data;
      console.log("res", res);
    } catch (error) {
      console.log(error);
    }
  },

  components: {
    EndSlot
  }
};
</script>

<style lang="scss">
.end {
  margin-top: 50px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  min-width: 1200px;
  min-height: 100%;
  .bannerBox {
    width: 40%;
  }
  .imgBox {
    height: 200px;
    margin: 10px 0;
  }
  .imgBox:nth-child(even) {
    margin-left: 20px;
  }
  .imgBox:nth-child(odd) {
    margin-right: 20px;
  }
}
</style>