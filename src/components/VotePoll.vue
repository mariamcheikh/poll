<template>
  <body>
    <div id="myform">
      <label> {{ question }} </label>

      <div v-for="answer in answers" :key="answer">
        <label>{{ answer.answer }}</label>
        <input
          type="radio"
          id=""
          name="answer"
          :value="answer.answer"
          v-model="selectedQuestion"
        />
      </div>

      <button @click="handleVote">Vote</button>
    </div>
  </body>
</template>
<script>
export default {
  components: {},
  data() {
    return {
      selectedQuestion: "",
      vote: {},
    };
  },
  props: ["question", "answers"],
  methods: {
    handleVote() {
      this.vote[this.selectedQuestion]
        ? this.vote[this.selectedQuestion]++
        : (this.vote[this.selectedQuestion] = 1);
      this.$emit("onChangeVote", this.vote);
      console.log(this.vote);
    },
  },
};
</script>
