<template>
  <div class="text-center">
    <h2 class="text-3xl font-bold mt-4 mb-10">Season: {{ season }}</h2>
  </div>
</template>

<script>
export default {
  name: "SeasonTitle",
  props: ["season"],
};
</script>
