<template>
  <div class="exhibition">
    <div class="menu">
      <!-- 스타일 바인딩 과제 -->
      <div @click="routerPush('ing')" :class="{ ingMenu: this.$route.name === 'ing', notIng: this.$route.name !== 'ing'}">
        <p>진행중</p>
      </div>
      <div @click="routerPush('end')" :class="{ ingMenu: this.$route.name === 'end', notIng: this.$route.name !== 'end'}">
        <p>종료</p>
      </div>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: "exhibition",
  data() {
    return {

    };
  },
  methods: {
    // 스타일 바인딩 과제 중 router 고정 문제
    routerPush(path){
      if(path !== this.$router.params){
        return this.$router.push(path).catch(()=>{})
      }
    }
  }
};
</script>
<style lang="scss" scoped>
.exhibition {
  max-width: 1220px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  .menu {
    width: 100%;
    height: 60px;
    display: flex;
    justify-content: center;
    align-content: center;
    cursor: pointer;
  }
  .ingMenu,
  .endMenu {
    width: 50%;
    text-align: center;

    font-size: 15px;
    line-height: 60px;
    border-bottom: 2px solid #ff204b;
    color: #ff204b;
    border-color: #ff204b;

    p {
      margin: unset
    }
  }
  .notIng, .notEnd {
    width: 50%;
    text-align: center;

    font-size: 15px;
    line-height: 60px;
    border-bottom: 1px solid lightgray;
    color: lightgray;
    border-color: lightgray;

    p {
      margin: unset
    }
  }
}
</style>

