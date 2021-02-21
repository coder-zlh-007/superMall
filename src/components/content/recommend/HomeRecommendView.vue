<template>
  <div>
      <recommend-view class="recommend">
          <recommend-item-view v-for="recommend in recommends" :key="recommend.image" class="recommend-item">
              <a :href="recommend.link">
                  <img :src="recommend.image" :alt="recommend.title">
              </a>
              <div>{{recommend.title}}</div>
          </recommend-item-view>
      </recommend-view>
  </div>
</template>

<script>
import {RecommendView, RecommendItemView} from "@/components/common/recommend"
export default {
    name: "HomeRecommendView",
    props: {
        recommends: {
            type: Array,
            default: () => []
        },
    },
    components: {
        RecommendView,
        RecommendItemView
    },
}

</script>
<style scoped>
    .recommend{
        display: flex;
        text-align: center;
        font-size: 12px;
        padding: 10px 0px 20px;
        border-bottom: 5px solid #eee;
    }

    .recommend-item{
        flex: 1;
    }

    img{
        width: 80px;
        height: 80px;
        margin-bottom: 5px;
    }
</style>