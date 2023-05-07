<template>
  <div class="courseCard">
    <NuxtLink :to="`/course/${course.courseID}`">
      <img :src="course.CourseThumb" :alt="course.CourseName" />

      <h2>
        {{ course.CourseName }}
      </h2>
      <p>
        By <b> {{ course.Author }} </b>
      </p>
      <p>
        LastUpdate:
        <b>
          {{ course.LastUpdate }}
        </b>
      </p>
      <p>
        Student: <b> {{ course.studentEnrolled }} </b>
      </p>
    </NuxtLink>
  </div>
</template>

<script setup>
// define props
const props = defineProps({
  course: {
    type: Object,
    required: true,
  },
});
</script>

<style scoped>
h2 {
  font-size: 1rem;
  margin: 0;
  margin-bottom: 0.5rem;
  color: #333;
}
a {
  text-decoration: none;
  color: #333;
}
.courseCard {
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 1rem;
  margin: 1rem;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
}
.courseCard:hover {
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.3);
}
img {
  width: 100%;
  height: 200px;
  object-fit: cover;
  margin-bottom: 1rem;
  border-radius: 5px;
}
</style>
