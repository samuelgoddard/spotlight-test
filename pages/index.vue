<template>
  <div>
    <h1>Spotlight [Sector]</h1>
    <h2>Our Locations</h2>

    <ul>
      <li v-for="page in pages" :key="page.path">
        <nuxt-link :to="page.permalink">
          {{ page.permalink }}
        </nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  asyncData: async ({ app, route, payload }) => {
    return {
      pages: (await app.$content("/locations").get(route.path)) || payload
    };
  }
};
</script>
