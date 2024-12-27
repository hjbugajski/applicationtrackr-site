<script lang="js" setup>
defineProps({
  backgroundClass: {
    type: Boolean,
    default: false
  },
  color: {
    type: String,
    default: 'neutral'
  },
  imageDark: {
    type: String,
    default: ''
  },
  imageLight: {
    type: String,
    default: ''
  },
  reverse: {
    type: Boolean,
    default: false
  }
});
</script>

<template>
  <section
    :class="[
      'at-feature',
      `at-color-${color}`,
      backgroundClass ? 'at-alpha-background' : undefined
    ]"
  >
    <div :class="['at-feature-inner-container', reverse ? 'at-feature-reverse' : undefined]">
      <div>
        <h2
          :class="[
            'at-gradient-header',
            `at-color-${color}`,
            reverse ? 'at-gradient-header--reverse' : undefined
          ]"
        >
          <ContentSlot :use="$slots.header" unwrap="p" />
        </h2>
        <slot name="description" />
      </div>
      <img
        :src="'/images/' + imageDark"
        class="at-feature-image at-dark-image at-border at-color-border"
      />
      <img
        :src="'/images/' + imageLight"
        class="at-feature-image at-light-image at-border at-color-border"
      />
    </div>
  </section>
</template>

<style lang="scss" scoped>
.at-feature {
  padding: 24px;
  border-radius: 24px;

  h2 {
    margin-bottom: 0;
  }

  @media (width >= 768px) {
    padding: 64px 24px;
  }
}

.at-feature-inner-container {
  display: grid;
  gap: 24px;
  align-items: center;
  justify-content: center;

  max-width: 1200px;
  margin: 0 auto;

  .at-feature-image {
    width: 100%;
    max-width: 675px;
    margin: 0 auto;
    border-radius: 10px;
  }

  @media (width >= 992px) {
    grid-template-columns: 1fr 675px;
    gap: 64px;

    &.at-feature-reverse {
      grid-template-columns: 675px 1fr;

      .at-feature-image {
        order: -1;
      }
    }
  }
}
</style>
