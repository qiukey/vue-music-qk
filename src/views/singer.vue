<template>
  <div class="singer" v-loading="!singers.length > 0">
    <index-list :data="singers"></index-list>
  </div>
</template>

<script>
import { getSingerList } from '@/service/singer'
import IndexList from '@/components/index-list/index-list'

export default {
  data() {
    return {
      singers: []
    }
  },
  components: {
    IndexList
  },
  created() {
    getSingerList().then(res => {
      this.singers = res.singers
    })
  }
}
</script>
<style lang='scss' scoped>
  .singer {
    position: fixed;
    top: 88px;
    width: 100%;
    bottom: 0;
  }
</style>
