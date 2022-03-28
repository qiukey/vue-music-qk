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
    },
    probeType: {
      type: Number,
      default: 0
    }
  },
  emits: ['scroll'],
  setup(props, { emit }) {
    const rootRef = ref(null)
    const scroll = ref(null)

    onMounted(() => {
      scroll.value = new BScroll(rootRef.value, {
        observeDOM: true,
        ...props
      })
      if (props.probeType > 0) {
        scroll.value.on('scroll', (pos) => {
          emit('scroll', pos)
        })
      }
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
