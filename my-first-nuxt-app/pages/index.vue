<template>
  <div>トップページ</div>
</template>

<script>
export default {
  async asyncData({ app }) {
    const items = await app.$axios.$get(
      "https://qiita.com/api/v2/items?query=tag:nuxt.js"
    );
    return {
      items,
    };
  },
};
</script>

