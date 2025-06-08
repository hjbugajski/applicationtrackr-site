<script lang="js" setup>
defineProps({
  color: {
    type: String,
    default: 'neutral'
  },
  icon: {
    type: String,
    default: ''
  }
});
</script>

<template>
  <div class="at-additional-feature at-alt-background">
    <div class="at-additional-feature-title-container">
      <div
        :class="[
          'at-additional-feature-icon-container',
          'at-alpha-background',
          `at-color-${color}`
        ]"
      >
        <span :class="['material-symbols-rounded', 'at-text', `at-color-${color}`]">{{
          icon
        }}</span>
      </div>
      <h3 :class="['at-text', `at-color-${color}`]">
        <slot name="header" mdc-unwrap="p" />
      </h3>
    </div>
    <p class="at-text muted">
      <slot name="description" mdc-unwrap="p" />
    </p>
  </div>
</template>

<style lang="scss" scoped>
.at-additional-feature {
  padding: 24px;
  border-radius: 24px;

  .at-additional-feature-title-container {
    display: flex;
    flex-direction: column;
    gap: 12px;
    margin-bottom: 16px;

    h3 {
      margin-bottom: 0;
    }

    @media (width >= 600px) {
      flex-direction: row;
      align-items: center;
    }
  }

  .at-additional-feature-icon-container {
    display: flex;
    align-items: center;

    width: fit-content;
    padding: 12px;
    border-radius: 12px;
  }

  .material-symbols-rounded {
    width: 24px;
    height: 24px;
  }

  p {
    margin: 0 !important;
  }
}
</style>
