<template>
  <div class="ctr">
    <div class="questions-ctr">
      <div class="progress">
        <div class="bar"></div>
        <div class="status">1 of 3 questions answered</div>
      </div>
      <div class="single-question">
        <div class="question">Sample Question 1</div>
        <div class="answers">
          <div class="answer">Sample Answer 1</div>
          <div class="answer">Sample Answer 2</div>
          <div class="answer">Sample Answer 3</div>
          <div class="answer">Sample Answer 4</div>
        </div>
      </div>
    </div>
    <div class="result">
      <div class="title">You got sample result 1</div>
      <div class="desc">
        short description about the result
      </div>
    </div>
    <button type="reset" class="reset-btn">Reset</button>
  </div>
</template>

<script>
 export default {
  name: 'App'
 }
</script>
