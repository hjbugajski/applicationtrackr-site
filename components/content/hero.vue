<script lang="ts" setup>
defineProps({
  color: {
    type: String,
    default: 'blue'
  },
  imageDark: {
    type: String,
    default: ''
  },
  imageLight: {
    type: String,
    default: ''
  },
  link: {
    type: Object,
    default: () => {}
  },
  reverse: {
    type: Boolean,
    default: false
  },
  type: {
    type: String,
    default: 'image'
  }
});
</script>

<template>
  <section>
    <div
      :class="['at-hero', 'at-alpha-background', `at-color-${color}`, type === 'image' ? 'at-hero--image' : undefined]"
    >
      <div class="at-hero-text">
        <h1 :class="['at-gradient-header', `at-color-${color}`, reverse ? 'at-gradient-header--reverse' : undefined]">
          <ContentSlot :use="$slots.header" unwrap="p" />
        </h1>
        <slot name="description" />
      </div>
      <NuxtLink
        v-if="type === 'link'"
        :to="link.to"
        :class="['at-button', 'at-flat-button', 'at-button--link', 'at-button--large', `at-color-${color}`]"
      >
        {{ link.text }}
      </NuxtLink>
    </div>
    <div v-if="type === 'image'" class="at-hero-center-image-container">
      <img :src="'/images/' + imageDark" class="at-hero-center-image at-dark-image at-border at-color-border" />
      <img :src="'/images/' + imageLight" class="at-hero-center-image at-light-image at-border at-color-border" />
    </div>
  </section>
</template>

<style lang="scss" scoped>
.at-hero {
  display: flex;
  flex-direction: column;
  gap: 16px;
  align-items: center;
  justify-content: center;
  padding: 24px;
  border-radius: 24px;

  &.at-hero--image {
    padding: 24px 24px 64px;
  }

  @media (width >= 768px) {
    padding: 64px 24px;

    &.at-hero--image {
      padding: 64px 24px 128px;
    }
  }
}

.at-hero-text {
  max-width: 768px;
  margin: 0 auto;
  text-align: center;

  h1 {
    margin-bottom: 8px;
  }
}

.at-hero-center-image-container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 24px;
  transform: translateY(-64px);

  .at-hero-center-image {
    width: 100%;
    border-radius: 10px;
  }

  @media (width >= 768px) {
    transform: translateY(-112px);
  }
}
</style>
