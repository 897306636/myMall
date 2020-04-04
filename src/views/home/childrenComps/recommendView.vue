<template>
    <div class="recommend">
        <div v-for="item in recommends" v-bind:key="item.image" class="recommend-item">
            <a :href="item.link">
                <img :src="item.image">
                <div class="title">{{item.title}}</div>
            </a>
        </div>
    </div>
</template>

<script>
  export default {
    name: "recommendView",
    props:{
        recommends:{
            type:Array,
            default() {
              return [];
            }
        }
    }
  }
</script>

<style scoped>
    .recommend{
        display:flex ;
        text-align: center;
        font-size: 12px;
        padding: 10px 0 20px;
        /*box-shadow: 0 1px 8px rgba(100,100,100,.1);*/
        border-bottom: 8px solid #eee;
    }
    .recommend-item{
        flex: 1;
    }
    .recommend img{
        width: 75px;
        height: 75px;
        margin-bottom: 10px;
    }
</style>