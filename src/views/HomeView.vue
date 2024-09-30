<template>
  <div class="container">
    <h1>Home</h1>
    <p>Welcome to the home page</p>
  </div>
</template>

<style>
.container {
  border: white solid 1px;
  border-radius: 15px;

  max-width: 80%;
  margin: 0 auto;
  padding: 1rem;
}
@media (min-width: 1024px) {
  .container {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
