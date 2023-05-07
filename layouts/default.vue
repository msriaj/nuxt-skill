<template>
  <div class="container">
    <Navbar />
    <div class="main">
      <slot />
    </div>
    <Footer />
  </div>
</template>
<style>
.main {
  padding: 1rem;
  overflow: hidden;
}
</style>
