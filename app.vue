<template>
  <div class="app-container">
    <nav class="at-toolbar">
      <NuxtLink to="/" class="at-button at-button--link at-button--left-icon at-button--large">
        <span class="material-symbols-rounded"> explore </span>
        ApplicationTrackr
      </NuxtLink>
      <NuxtLink to="https://app.applicationtrackr.io/" class="at-button at-button--link"> Sign in </NuxtLink>
    </nav>
    <main class="nuxt-page-container">
      <NuxtPage />
    </main>
    <footer class="at-footer">
      <NuxtLink to="/privacy-policy" class="at-button at-button--link"> Privacy policy </NuxtLink>
    </footer>
  </div>
</template>

<style lang="scss">
.at-toolbar {
  position: sticky;
  top: 0;
  z-index: 2;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  height: 64px;
  padding: 0 8px;
  background-color: var(--color-backdrop);
  border-bottom: 2px solid var(--color-border);
  backdrop-filter: saturate(180%) blur(20px);
  transition-property:
    background-color,
    backdrop-filter,
    -webkit-backdrop-filter;
}

.nuxt-page-container {
  display: flex;
  flex: 1;
  flex-direction: column;
  padding: 8px;

  @media (width >= 768px) {
    padding: 16px;
  }
}

.at-footer {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  min-height: 64px;
  padding: 8px;
  background-color: var(--color-canvas);
  border-top: 2px solid var(--color-border);
}
</style>
