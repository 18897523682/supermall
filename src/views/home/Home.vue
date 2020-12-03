<template>
    <div id="home">
      <nav-bar  class="home-nav">
        <div slot="center">购物街</div>
      </nav-bar>
      <home-swiper :banners="banners"/>
      <recommend-view :recommends="recommends"/>
    </div>
</template>

<script>
  import NavBar from "components/common/navbar/NavBar";
  import HomeSwiper from "./childCoponents/HomeSwiper";
  import RecommendView from "./childCoponents/RecommendView";

  import {getHomeMultdata} from "../../network/home";


  export default {
      name: "Home",
    data() {
        return {
          banners: [],
          recommends: []
        }
    },
      components: {
        NavBar,
        HomeSwiper,
        RecommendView
      },
    created() {

        getHomeMultdata().then(res => {
          this.banners = res.data.data.banner.list
          this.recommends = res.data.data.recommend.list
          console.log(this.banners);
          console.log(this.recommends);
        })
    }
  }
</script>

<style scoped>
  .home-nav {
    background-color: var(--color-tint);
    color: #ffffff;
  }
</style>
