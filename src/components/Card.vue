<template>
  <div class="card-container">
    <div v-if="!isSubmit" class="card-wrapper">
      <div class="icon-star-container">
        <img src="../assets/icon-star.svg" alt="icon-star" />
      </div>
      <h1>How did we do ?</h1>
      <span>
        Please let us know how we did with your support request. All feedback is
        appreciated to help us improve our offering!
      </span>
      <div class="score-container">
        <div
          v-for="item in scoreList"
          :key="item"
          v-bind:class="{ active: score === item }"
          class="score-card-container"
          @click="setScore(item)"
        >
          <span>{{ item }}</span>
        </div>
      </div>
      <button @click="onSubmit">submit</button>
    </div>
    <div v-else class="card-wrapper-submit">
      <img src="../assets/illustration-thank-you.svg" alt="thank-you" />
      <div class="score-result">
        <span>You selected {{ score }} out of 5</span>
      </div>
      <h1>Thank you!</h1>
      <span class="desc">
        We appreciate you taking the time to give a rating. If you ever need
        more support, don't hesitate to get in touch!
      </span>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component
export default class Card extends Vue {
  scoreList = [1, 2, 3, 4, 5];
  score: number | null = null;
  isSubmit = false;

  setScore(number: number): void {
    this.score = number;
  }

  onSubmit(): void | null {
    if (!this.score) return;
    this.isSubmit = true;
  }
}
</script>

<style scoped lang="scss">
.card-container {
  width: 420px;
  height: 420px;
  background-color: hsl(213, 19%, 18%);
  border-radius: 2rem;

  .card-wrapper {
    width: 100%;
    height: 100%;
    padding: 2rem;
    display: flex;
    flex-direction: column;
    justify-content: space-between;

    .icon-star-container {
      width: 50px;
      height: 50px;
      background-color: hsl(218, 18%, 24%);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .score-container {
      display: flex;
      justify-content: space-between;

      .score-card-container {
        width: 50px;
        height: 50px;
        background-color: hsl(218, 18%, 24%);
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;

        &.active {
          background-color: hsl(25, 97%, 53%);
          span {
            color: hsl(0, 0%, 100%);
          }
        }

        &:hover {
          background-color: hsl(216, 12%, 54%);

          span {
            color: hsl(0, 0%, 100%);
          }
        }
      }
    }

    h1 {
      color: hsl(0, 0%, 100%);
    }

    span {
      font-weight: 700;
      line-height: 1.5rem;
      color: hsl(217, 12%, 63%);
    }

    button {
      padding: 0.8rem 0;
      border-radius: 35px;
      border: none;
      text-transform: uppercase;
      background-color: hsl(25, 97%, 53%);
      color: hsl(0, 0%, 100%);
      font-size: 1rem;
      font-family: inherit;
      font-weight: 700;
      letter-spacing: 0.15rem;
      cursor: pointer;

      &:active {
        background-color: hsl(0, 0%, 100%);
        color: hsl(25, 97%, 53%);
      }
    }
  }

  .card-wrapper-submit {
    width: 100%;
    height: 100%;
    padding: 1.5rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-around;

    img {
      width: 40%;
    }

    .score-result {
      border-radius: 25px;
      background-color: hsl(218, 18%, 24%);
      display: flex;

      span {
        color: hsl(25, 97%, 53%);
        font-weight: 400;
        padding: 0.35rem 1rem;
      }
    }

    h1 {
      color: hsl(0, 0%, 100%);
    }

    .desc {
      text-align: center;
      font-weight: 700;
      color: hsl(217, 12%, 63%);
      margin-top: -30px;
    }
  }
}

@media (max-width: 375px) {
  .card-container {
    width: 350px;
  }
}
</style>
