<template>
    <div class="tab-bar-item" @click="clickTabBarItem">
      <div v-if="isActive">
           <slot name="item-icon"></slot>
      </div>
      <div v-else>
          <slot name="item-icon-active"></slot>
      </div>
      <div :style="colorStyle">
          <slot name="item-text"></slot>
      </div>
    </div>
</template>

<script>
export default {
    name: 'TabBarItem',
    props: {
        path: String,
        colorStyleValue: {
            type: String,
            default: 'salmon'
        }
    },
    data() {
        return {
            //isActive: true
        }
    },
    methods: {
        clickTabBarItem() {
            console.log(this.path);
            this.$router.replace(this.path);
        }
    },
    computed: {
        isActive() {
            return this.$route.path.indexOf(this.path) === -1; 
        },
        colorStyle() {
            return !this.isActive ? {color: this.colorStyleValue} : {}
        }
    },
}
</script>

<style>
     .tab-bar-item {
    flex: 1;
    text-align: center;
    height: 49px;
  }

  .tab-bar-item img{
    width: 24px;
    height: 24px;
     margin-top: 3px;
    vertical-align: middle;
  }
</style>