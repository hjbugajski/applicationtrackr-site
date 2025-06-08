<script setup lang="js">
const route = useRoute();
const { data } = await useAsyncData(route.path, () => {
  return queryCollection('content').path(route.path).first();
});

useSeoMeta({
  titleTemplate:
    data.value?.title && data.value.title !== 'ApplicationTrackr'
      ? `${data.value.title} | ApplicationTrackr`
      : 'ApplicationTrackr',
  description: data.value?.description
});
</script>

<template>
  <ContentRenderer v-if="data" :value="data" :class="[data?.class ?? undefined]" />
  <div v-else>
    <h1 style="margin: 64px 0; text-align: center">404 | Page not found</h1>
  </div>
</template>
