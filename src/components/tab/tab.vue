<template>
  <div class="tab">
    <router-link class="tab-item" v-for="tab in tabs" :key="tab.path" :to="tab.path">
      <span class="tab-link">
        {{tab.name}}
      </span>
    </router-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tabs: [
        {
          name: '推荐',
          path: '/recommend'
        },
        {
          name: '歌手',
          path: '/singer'
        },
        {
          name: '排行',
          path: '/top-list'
        },
        {
          name: '搜索',
          path: '/search'
        }
      ]
    }
  }
}
</script>
<style  lang='scss' scoped>
</style>
