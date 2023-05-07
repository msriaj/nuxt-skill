<template>
  <NuxtLayout>
    <Transition @enter="enter" @leave="leave" mode="out-in">
      <NuxtPage />
    </Transition>
  </NuxtLayout>
</template>

<script setup>
import gsap from "gsap";

const enter = (el, done) => {
  gsap.from(el, {
    duration: 1,
    x: 50,
    opacity: 0,
    ease: "power2.inOut",
    delay: 0.5,
    stagger: 0.2,
    onComplete: done,
  });
};

const leave = (el, done) => {
  gsap.to(el, {
    duration: 1,
    x: -50,
    opacity: 0,
    ease: "power2.easeInOut",
    delay: 0.5,
    stagger: 0.2,
    onComplete: done,
  });
};
</script>
<style>
* {
  box-sizing: border-box;

  margin: 0;
  padding: 0;
}
body {
  margin: 0;
  padding: 0;
  font-family: sans-serif;
  background-color: aliceblue;
}
.container {
  max-width: 1200px;
  margin: 0 auto;
  background-color: #fff;
}
</style>
