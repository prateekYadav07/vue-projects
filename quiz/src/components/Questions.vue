<template>
  <div class="questions-ctr">
    <div class="progress">
      <div
        class="bar"
        :style="{ width: `${(currQues / questions.length) * 100}%` }"
      ></div>
      <div class="status">
        {{ qAns }} of {{ questions.length }} questions answered
      </div>
    </div>
    <TransitionGroup name="fade" mode="out-in">
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
    </TransitionGroup>
  </div>
  <div class="cont-btns">
    <button type="button" class="btn reset-btn" @click="previous">
      Previous
    </button>
    <button type="button" class="btn reset-btn" @click="next">Next</button>
  </div>
</template>

<script>
import { TransitionGroup } from 'vue';

export default {
    name: "vQuestions",
    props: {
        questions: Array,
        qAns: Number,
        currQues: Number,
    },
    emits: ["answerSelected", "next", "previous"],
    methods: {
        answerSelected(answer) {
            this.$emit("answerClicked", answer);
        },
        next() {
            this.$emit("next");
        },
        previous() {
            this.$emit("previous");
        },
    },
    computed: {
        currentQuestion() {
            return this.questions[this.currQues < this.questions.length
                ? this.currQues
                : this.questions.length - 1];
        },
    },
    components: { TransitionGroup }
};
</script>
