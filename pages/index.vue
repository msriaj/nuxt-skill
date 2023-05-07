<template>
  <div class="homeTopContent">
    <h1>Welcome to SkillUp</h1>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam
      voluptatibus, quibusdam, quia, voluptatem voluptatum quod quos voluptates
      quas quibusdam, quia, voluptatem voluptatum quod quos voluptates quas
    </p>
  </div>
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
import gsap from "gsap";
import CourseCard from "~/components/Card/CourseCard.vue";
const { data } = await useFetch(
  `https://skillup-server-msriaj.vercel.app/category/7`
);

useHead({
  title: "SkillUp",
});

onMounted(() => {
  gsap.from(".card", {
    duration: 1,
    y: 200,
    opacity: 0,
    scale: 0,
    ease: "power4.inOut",
    delay: 0.3,
    stagger: 0.1,
  });

  gsap.from(".homeTopContent h1", {
    duration: 1,
    y: 200,
    opacity: 0,
    ease: "power4.inOut",
  });
  gsap.from(".homeTopContent p", {
    duration: 1,
    y: 200,
    opacity: 0,
    ease: "power4.inOut",
    delay: 0.2,
  });
});
</script>

<style>
.cards {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1rem;
}
.homeTopContent {
  padding: 1rem;
  color: #666;
  text-align: center;
}
.homeTopContent h1 {
  font-size: 3rem;
  margin: 0;
  color: #333;
  padding: 1rem;
}
.homeTopContent p {
  max-width: 70%;

  margin: 0 auto;
}
</style>
