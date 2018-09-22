<template>
  <div 
    class="card" 
    :class="'card--' + size"
  >
    <slot />
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    size: {
      type: String,
      default: 'small'
    }
  }
}
</script>

<style lang="scss">
@import '@design';

.card {
  width: 100%;
  height: auto;
  min-height: 100px;
  margin: 10px 20px;
  border: 1px #ececec solid;
  background: white;
  padding: 25px 30px;
  border-radius: 5px;
  box-shadow: 1px 1px rgba($color-black, 0.04);

  &--small {
    max-width: 32rem;
  }

}
</style>