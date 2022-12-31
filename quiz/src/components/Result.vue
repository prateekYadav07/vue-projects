<template>
  <div class="result" v-for="result in results" :key="result.title">
    <template v-if="result['min'] <= currAns && currAns <= result['max']">
      <div class="title">{{result['title']}}</div>
      <div class="desc">{{result['desc']}}</div>
    </template>
  </div>
</template>

<script>
export default {
  name: "vResult",
  props: {
    currAns: Number,
    results: Array,
  },
};
</script>
