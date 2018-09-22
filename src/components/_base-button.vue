<template>
  <button
    :class="$style.button"
    v-on="$listeners"
  >
    <slot />
  </button>
</template>

<style lang="scss" module>
@import '@design';

.button {
  @extend %typography-small;

  display: inline-block;
  width: 100%;
  padding: $size-button-padding;
  color: $color-button-text;
  cursor: pointer;
  background: $color-button-bg;
  border: none;
  border-radius: 20px;

  &:disabled {
    cursor: not-allowed;
    background: $color-button-disabled-bg;
  }
}
</style>
