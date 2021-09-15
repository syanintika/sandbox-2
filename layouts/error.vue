<template>
  <div>
    <div v-if="error.statusCode === 404">
      <img class="w-100" src="https://www.f-nakata.com/wp-content/uploads/2021/02/Cara-Masuk-Website-Yang-Sibuk-2.png" alt="">
    </div>
    <div v-else>An error occurred</div>
    <div class="text-center">
      <NuxtLink to="/">Home page</NuxtLink>
    </div>
  </div>
</template>

<script>
export default {
  props: ["error"],
  layout: "clean", // you can set a custom layout for the error page
};
</script>