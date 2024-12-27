<script setup lang="js">
const title = 'ApplicationTrackr';

useHead({
  titleTemplate: (pageTitle) => {
    return !pageTitle || pageTitle === title ? title : `${pageTitle} | ${title}`;
  }
});
</script>

<template>
  <ContentDoc>
    <template #default="{ doc }">
      <ContentRenderer :value="doc" :class="[doc?.class ?? undefined]" />
    </template>
    <template #not-found>
      <h1 style="margin: 64px 0; text-align: center">404 | Page not found</h1>
    </template>
  </ContentDoc>
</template>
