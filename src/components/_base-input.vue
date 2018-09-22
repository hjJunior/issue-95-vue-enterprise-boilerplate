<script>
export default {
  props: {
    type: {
      type: String,
      default: 'text',
    },
    placeholder: {
      type: String,
      default: '',
    },
    value: {
      type: [String, Number],
      default: '',
    },
  },
  computed: {
    listeners() {
      return {
        ...this.$listeners,
        input: event => this.$emit('input', event.target.value),
      }
    },
  },
}
</script>

<template>
  <input
    :type="type"
    :value="value"
    :class="$style.input"
    :placeholder="placeholder"
    v-on="listeners"
  >
</template>

<style lang="scss" module>
@import '@design';

.input {
  @extend %typography-small;

  display: block;
  width: 100%;
  padding: $size-input-padding-vertical $size-input-padding-horizontal;
  margin-bottom: $size-grid-padding;
  line-height: 1;
  background: transparent;
  border: 0;
  border-bottom: 1px solid #ececec;
}
</style>
