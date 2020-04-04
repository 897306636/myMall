<template>
    <div id="home">
        <navbar class="home-nav"><div slot="center">购物街</div></navbar>
        <HomeSwiper :banners="banners"></HomeSwiper>
        <recommend-view  :recommends="recommends"></recommend-view>
        <feature-view></feature-view>
        
    </div>
</template>

<script>
import navbar from "components/common/navbar/navbar";
import HomeSwiper from "./childrenComps/HomeSwiper";
import recommendView from "./childrenComps/recommendView";
import featureView from "./childrenComps/featureView";
import {getHomeMultidata} from "../../network/home";

export default {
    name: "Home",
    components:{
        navbar,
        HomeSwiper,
        recommendView,
        featureView
    },
    data(){
        return{
          banners:[],
          recommends:[]
        }
    },
    created() {
        //请求多个数据
        getHomeMultidata().then(res=>{
            //console.log(res.data)
            this.banners = res.data.banner.list;
            this.recommends = res.data.recommend.list
        })
    }
}
</script>

<style scoped>
    #home{
       padding-top:44px;
    }
    .home-nav{
        background-color: var(--color-tint);
        color: #fff;
        position: fixed;
        left: 0;
        right: 0;
        top: 0;
        z-index: 9;
    }
</style>