<template>
  <div class="ctr">
    <QuestionsVue
      v-if="questionsAnswered < questions.length"
      :qAns="questionsAnswered"
      :questions="questions"
      :currQues="currentQuestion"
      @answerClicked="answered"
      @next="next"
      @previous="previous"
    ></QuestionsVue>
    <ResultVue v-else :results="results" :currAns="correctAnswers"></ResultVue>
    <button
      type="reset"
      class="reset-btn"
      v-show="hideTheReset"
      @click.prevent="reset"
    >
      Reset
    </button>
  </div>
</template>

<script>
import QuestionsVue from "./components/Questions.vue";
import ResultVue from "./components/Result.vue";

export default {
  name: "App",
  components: {
    QuestionsVue,
    ResultVue,
  },
  data() {
    return {
      currentQuestion: 0,
      questionsAnswered: 0,
      correctAnswers: 0,
      questions: [
        {
          q: "What is 2+2",
          answers: [
            {
              text: 4,
              is_correct: true,
            },
            {
              text: 3,
              is_correct: false,
            },
            {
              text: "Fish",
              is_correct: false,
            },
            {
              text: 5,
              is_correct: false,
            },
          ],
        },
        {
          q: "How Many letters in Banana",
          answers: [
            {
              text: 6,
              is_correct: true,
            },
            {
              text: 3,
              is_correct: false,
            },
            {
              text: "Fish",
              is_correct: false,
            },
            {
              text: 5,
              is_correct: false,
            },
          ],
        },
        {
          q: "What is 7*7",
          answers: [
            {
              text: 4,
              is_correct: false,
            },
            {
              text: 49,
              is_correct: true,
            },
            {
              text: "Fish",
              is_correct: false,
            },
            {
              text: 5,
              is_correct: false,
            },
          ],
        },
      ],
      results: [
        {
          min: 0,
          max: 2,
          title: "Try again!",
          desc: "Do a little more studying",
        },
        {
          min: 3,
          max: 3,
          title: "genius",
          desc: "bWAAAHHHHHHHHHHHHHHh",
        },
      ],
    };
  },
  methods: {
    answered(ans) {
      this.currentQuestion += 1;
      this.questionsAnswered += 1;
      if (ans["is_correct"]) {
        this.correctAnswers += 1;
      }
    },
    reset() {
      this.questionsAnswered = 0;
      this.currentQuestion = 0;
      this.correctAnswers = 0;
    },

    next() {
      if (
        this.questionsAnswered < this.questions.length &&
        this.currentQuestion < this.questions.length
      ) {
        this.currentQuestion += 1;
      }
    },
    previous() {
      if (this.currentQuestion > 0) {
        this.currentQuestion -= 1;
      }
    },
  },
  computed: {
    hideTheReset() {
      return this.questionsAnswered === this.questions.length ? true : false;
    },
  },
};
</script>
