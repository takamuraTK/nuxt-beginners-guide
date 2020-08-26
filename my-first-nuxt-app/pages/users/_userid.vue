<template>
  <section class="container">
    <div>User ID: {{user.id}}</div>
    <img :src="user.profile_image_url" width="120" alt />
  </section>
</template>

<script>
export default {
  head() {
    return {
      title: this.user.id,
    };
  },
  async asyncData({ route, app }) {
    const user = await app.$axios.$get(
      `https://qiita.com/api/v2/users/${route.params.userid}`
    );
    const items = await app.$axios.$get(
      `https://qiita.com/api/v2/items?query=user:${route.params.userid}`
    );
    return { user, items };
  },
};
</script>
