<script setup>
const route = useRoute();
const { data } = await useFetch(
  `https://skillup-server-msriaj.vercel.app/course/${route.params.id}`
);

useHead({
  title: "SkillUp",
});
import gsap from "gsap";

onMounted(() => {
  gsap.from(".main img", {
    duration: 1,
    y: 200,
    opacity: 0,
    ease: "power4.inOut",
  });
  gsap.from(".main h1", {
    duration: 1,
    y: 200,
    opacity: 0,
    ease: "power4.inOut",
    delay: 0.2,
  });
  gsap.from(".main .infos", {
    duration: 1,
    y: 200,
    opacity: 0,
    ease: "power4.inOut",
    delay: 0.3,
  });
  gsap.from(".main p", {
    duration: 1,
    y: 200,
    opacity: 0,
    ease: "power4.inOut",
    delay: 0.5,
  });

  gsap.from(".main h2", {
    duration: 1,
    y: 200,
    opacity: 0,
    ease: "power4.inOut",
    delay: 0.5,
  });

  gsap.from(".main ul", {
    duration: 1,
    y: 200,
    opacity: 0,
    ease: "power4.inOut",
    delay: 0.6,
  });
});
</script>
<template>
  <div class="main">
    <img :src="data.CourseThumb" />

    <h1>{{ data.CourseName }}</h1>

    <div class="infos">
      <span>
        By <b>{{ data.Author }}</b>
      </span>
      <span>Last Update: {{ data.LastUpdate }}</span>
      <span>Students: {{ data.studentEnrolled }}</span>
      <span>Category Name: {{ data.CategoryName }}</span>
      <span>
        Rating: <b>{{ data.Review }}</b>
      </span>
      <span>
        Hours: <b>{{ data.Hours }}</b>
      </span>
    </div>
    <h2>
      <b>Descriptions</b>
    </h2>
    <p>{{ data.descriptions }}</p>

    <h2>
      <b>Features</b>
    </h2>
    <ul>
      <li v-for="feature in data.Features" :key="feature">
        {{ feature }}
      </li>
    </ul>

    <h2>
      <b>What you'll learn</b>
    </h2>
    <ul>
      <li v-for="learn in data.whatWillLearn" :key="learn">
        {{ learn }}
      </li>
    </ul>
  </div>
</template>
<style>
.main {
  padding: 1rem;
  color: #666;
}
h2 {
  margin-top: 10px;
  color: #333;
}
img {
  width: 100%;
  object-fit: cover;
  margin-bottom: 1rem;
}
.infos {
  display: flex;
  justify-content: space-between;
  margin-bottom: 1rem;
  background-color: aliceblue;
  padding: 0.4rem;
  color: gray;
  margin-top: 1rem;
}
ul {
  padding-left: 30px;
  margin-top: 10px;
}
</style>
