<template>
  <div class="container">
    <span class="dot"></span>
    <p class="slogan">Show them your Quizz</p>
  </div>
</template>

<style>
.dot {
  height: 25px;
  width: 25px;
  background-color: #2e6464;
  border-radius: 50%;
  display: inline-block;
  text-align: center;
  margin: auto;
}
/* .dot later gets the icon/play button*/

.slogan {
  font-size: 1.5rem;
  color: #fff;
  text-align: center;
  padding: 1rem;
}

.container {
  border: white solid 1px;
  border-radius: 15px;

  max-width: 80%;
  min-height: 80vh;
  margin: 0 auto;
  padding: 1rem;

  display: flex;
  flex-direction: column;
  justify-content: flex-end;

  
}
@media (min-width: 1024px) {
  .container {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
