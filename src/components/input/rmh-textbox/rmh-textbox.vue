<template src="./rmh-textbox.html"></template>

<script>
import component from '@/mixins/component'
import rmhField from '../rmh-field/rmh-field'
import rmhIcon from '../rmh-icon/rmh-icon'

export default {
  name: 'rmh-textbox',

  mixins: [component],

  components: {
    rmhField,
    rmhIcon
  },

  props: {
    value: {
      type: [String, Number],
      default: ''
    },
    label: {
      type: String,
      default: ''
    },
    icon: {
      type: String,
      default: ''
    },
    disabled: {
      type: Boolean,
      default: false
    },
    bordered: {
      type: Boolean,
      default: false
    },
    required: {
      type: Boolean,
      default: false
    }
  },

  data: () => ({
    localValue: ''
  }),

  mounted () {
    this.localValue = this.value
    this.$refs.field.inputMounted(this.value)
  },

  computed: {
    listeners () {
      let l = { ...this.$listeners }
      delete l.input
      return l
    },

    classes () {
      return {
        'with-icon': this.icon !== '',
        'bordered': this.bordered,
        'disabled': this.disabled,
        'required': this.required
      }
    }
  },

  watch: {
    localValue (val) {
      this.$emit('input', val)
    },
    value (val) {
      this.localValue = val
    }
  },

  methods: {
    focus (e) {
      this.$refs.field.focus(e)
    },

    blur (e) {
      this.$refs.field.blur(e)
    }
  }
}
</script>

<style src="./rmh-textbox.styl" lang="stylus"></style>
