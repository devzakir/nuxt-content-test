<template>
  <div>
    <Tutorial/>
    <nuxt-content :document="page" />
  </div>
</template>

<script>
export default {
  async asyncData({ $content,  error }) {
    const page = await $content('hello')
      .fetch()
      .catch(err => {
        error({ statusCode: 404, message: "Page not found" });
      });

    return { page };
  }
};

</script>
