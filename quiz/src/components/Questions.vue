<template>
  <div class="questions-ctr">
    <div class="progress">
      <div class="bar"></div>
      <div class="status">
        {{ qAns }} of {{ questions.length }} questions answered
      </div>
    </div>
    <div class="single-question">
      <div class="question">{{ currentQuestion["q"] }}</div>
      <div
        class="answers"
        v-for="answer in currentQuestion['answers']"
        :key="answer.text"
      >
        <div class="answer" @click="answerSelected(answer)">
          {{ answer.text }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "vQuestions",
  props: {
    questions: Array,
    qAns: Number,
    currQues: Number,
  },
  methods: {
    answerSelected(answer) {
        this.$emit('answerClicked', answer)
    },
  },
  computed: {
    currentQuestion() {
      return this.questions[
        this.currQues < this.questions.length
          ? this.currQues
          : this.questions.length - 1
      ];
    },
  },
};
</script>
