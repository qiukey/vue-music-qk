<template>
  <div ref="rootRef">
    <slot></slot>
  </div>
</template>

<script>
import BScroll from '@better-scroll/core'
import ObserveDOM from '@better-scroll/observe-dom'
import { onMounted, onUnmounted, ref } from 'vue'

BScroll.use(ObserveDOM)

export default {
  name: 'scroll',
  props: {
    click: {
      type: Boolean,
      default: true
    }
  },
  setup(props) {
    const rootRef = ref(null)
    const scroll = ref(null)

    onMounted(() => {
      scroll.value = new BScroll(rootRef.value, {
        observeDOM: true,
        ...props
      })
    })

    onUnmounted(() => {
      scroll.value.destroy()
    })

    return {
      rootRef,
      scroll
    }
  }
}

</script>
<style lang='scss' scoped>
</style>
