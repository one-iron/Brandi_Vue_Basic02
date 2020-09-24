<template>
  <div class="ing">
    <div class="bannerBox" v-for="( banner ) in banners" v-bind:key="banner.id">
      <!-- 연동 2 과제 중 인라인 스타일 리터럴 문제 -->
      <div
        class="imgBox"
        :style="`backgroundImage: url(${banner.image_url}); backgroundSize: cover`"
        @click="likeHandle(banner.id)"
      >
      <!-- v-if 과제  -->
        <img
          v-if="likeState.indexOf(banner.id) > -1"
          src="https://www.flaticon.com/svg/static/icons/svg/929/929417.svg"
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      banners: [],
      likeState: []
    };
  },
  //연동 2 과제 중 axios 문제
  created: async function getBanners() {
    try {
      const res = await axios.get("/static/ingBannersImg.json");
      this.banners = res.data;
    } catch (error) {
      console.log(error);
    }
  },

  methods: {
    likeHandle(id) {
      let index = this.likeState.indexOf(id);
      index > -1 ? this.likeState.splice(index, 1) : this.likeState.push(id)
    }
  }
};
</script>

<style lang="scss">
.ing {
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
    position: relative;
    height: 200px;
    margin: 10px 0;
    cursor: pointer;
    img {
      position: absolute;
      right: 10px;
      bottom: 10px;
      width: 30px;
      opacity: 0.8;
    }
  }
  .imgBox:nth-child(even) {
    margin-left: 20px;
  }
  .imgBox:nth-child(odd) {
    margin-right: 20px;
  }
}
</style>