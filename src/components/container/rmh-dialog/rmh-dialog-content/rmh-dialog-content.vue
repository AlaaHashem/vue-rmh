<template src="./rmh-dialog-content.html"></template>

<script>
import component from '@/mixins/component'

export default {
  name: 'rmh-dialog-content',

  mixins: [component],

  computed: {
    hasDefaultSlot () {
      return !!this.$slots.default
    }
  }
}
</script>

<style src="./rmh-dialog-content.styl" lang="stylus"></style>
