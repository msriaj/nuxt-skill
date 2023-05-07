<template>
  <div>
    <NuxtLink to="/"> <h1 class="logo">SkillUp</h1></NuxtLink>
  </div>
  <div class="nav">
    <NuxtLink
      v-for="category in data"
      class="nav-item"
      :key="category.id"
      :to="`/category/${category.catID}`"
    >
      {{ category.CategoryName }}
    </NuxtLink>
  </div>
</template>

<script setup>
const { data } = await useFetch(
  "https://skillup-server-msriaj.vercel.app/categories"
);
import gsap from "gsap";
onMounted(() => {
  gsap.from(".nav-item", {
    duration: 1,
    x: 5,
    opacity: 0,

    ease: "power4.easeInOut",
    delay: 0.1,
  });
});
</script>

<style scoped>
a {
  display: block;
}
.logo {
  font-size: 3rem;
  margin: 0;
  color: #333;
  padding: 1rem;
}
.nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
  background-color: #333;
  color: #fff;
}
a {
  color: #fff;
  text-decoration: none;
}
a:hover {
  color: #ccc;
}
</style>
