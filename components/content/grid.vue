<template>
  <section class="at-grid">
    <slot />
  </section>
</template>

<style lang="scss" scoped>
.at-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 16px;

  max-width: 1200px;
  margin: 64px auto;

  @media (width >= 600px) {
    grid-template-columns: repeat(2, 1fr);
    gap: 32px;
  }
}
</style>
