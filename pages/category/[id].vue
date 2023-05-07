<template>
  <div class="cards">
    <CourseCard
      class="card"
      v-for="course in data"
      :key="course.catID"
      :course="course"
    />
  </div>
</template>
<script setup>
import CourseCard from "~/components/Card/CourseCard.vue";
const route = useRoute();
const { data } = await useFetch(
  `https://skillup-server-msriaj.vercel.app/category/${route.params.id}`
);

import gsap from "gsap";

onMounted(() => {
  gsap.from(".card", {
    duration: 1,
    scaley: 0,
    x: 200,
    opacity: 0,
    ease: "power2.inOut",
    delay: 0.2,
    stagger: 0.1,
  });
});
</script>

<style>
.cards {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1rem;
}
</style>
