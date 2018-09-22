<script>
import NavBar from '@components/nav-bar'

export default {
  components: { NavBar },
  props: {
    disabledNavBar: {
      default: false,
      type: Boolean
    }
  }
}
</script>

<template>
  <div :class="$style.container">
    <NavBar v-if="!disabledNavBar" />
    <slot />
  </div>
</template>

<style lang="scss" module>
@import '@design';

.container {
  min-width: $size-content-width-min;
  max-width: $size-content-width-max;
  margin: 0 auto;
}
</style>
