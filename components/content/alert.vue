<script lang="js" setup>
defineProps({
  backgroundClass: {
    type: Boolean,
    default: false
  },
  color: {
    type: String,
    default: 'neutral'
  }
});
</script>

<template>
  <section
    :class="[
      'at-alert',
      'at-border',
      `at-color-${color}`,
      backgroundClass ? 'at-alpha-background' : undefined
    ]"
  >
    <p :class="['at-text', `at-color-${color}`]">
      <slot name="description" mdc-unwrap="p" />
    </p>
  </section>
</template>

<style lang="scss" scoped>
.at-alert {
  padding: 24px;
  border-radius: 24px;

  p {
    margin: 0;
  }
}
</style>
