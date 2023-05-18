<template>
  <div class="panel" v-show="screen == 'rating'">
    <img class="star" src="../assets/icon-star.svg" alt="orange star" />

    <div class="content">
      <h1 class="title">How did we do?</h1>
      <p>
        Please let us know how we did with your support request. All feedback is
        appreciated to help us improve our offering!
      </p>
    </div>
    <div class="rating-buttons">
      <button @click="rating = 1" class="rating">1</button>
      <button @click="rating = 2" class="rating">2</button>
      <button @click="rating = 3" class="rating">3</button>
      <button @click="rating = 4" class="rating">4</button>
      <button @click="rating = 5" class="rating">5</button>
    </div>
    <button class="submit" @click="ratingSubmit()">SUBMIT</button>
  </div>

  <div class="thank-you" v-show="screen == 'thank you'">
    <img src="../assets/illustration-thank-you.svg" alt="thank you" />
    <p class="selected-rating">You selected {{ rating }} out of 5</p>
    <h1>Thank you!</h1>
    <p>
      We appreciate you taking the time to give a rating. It you ever need more
      support. don't hesitate to get in touch!
    </p>
  </div>
</template>

<script setup>
import { ref } from "vue";

const screen = ref("rating");
const rating = ref(0);

function ratingSubmit() {
  if (rating.value) screen.value = "thank you";
}
</script>

<style scoped>
.panel {
  width: 375px;
  height: 375px;
  background: linear-gradient(var(--gradient-1), var(--gradient-2));
  padding: 25px;
  border-radius: 1.5rem;
  display: grid;
  align-content: space-between;
}
.star {
  width: 40px;
  height: 40px;
  background: #262f38;
  border-radius: 100%;
  padding: 0.75rem;
}

.submit {
  height: 42px;
  border-radius: 2.5rem;
  background-color: var(--primary-color);
  color: white;
  border: 0;
  font-size: 0.875rem;
}

.title {
  font-size: 1.75rem;
  padding-bottom: 10px;
}

.content {
  margin: 1.5rem 0;
}

.rating {
  height: 45px;
  width: 45px;
  border-radius: 100%;
  color: #858d97;
  background-color: #262f38;
}

.rating-buttons {
  display: flex;
  justify-content: space-between;
  margin-bottom: 1.5rem;
}

.rating:hover,
.rating:focus {
  background-color: var(--medium-gray);
  color: white;
}

.rating:focus {
  background-color: var(--primary-color);
}

.submit:hover,
.submit:focus {
  background-color: white;
  color: var(--primary-color);
}

.thank-you {
  width: 375px;
  height: 375px;
  background: linear-gradient(var(--gradient-1), var(--gradient-2));
  padding: 35px 25px;
  border-radius: 1.5rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.selected-rating {
  color: #fc7614;
  background-color: var(--dark-blue);
  border-radius: 25px;
  padding: 5px 15px;
  margin: 1.6rem 0;
  font-size: 0.9375rem;
}

p {
  font-size: 0.9375rem;
  color: hsl(217, 12%, 63%);
}
</style>
