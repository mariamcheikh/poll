<template>
  <head>
    <link
      rel="stylesheet"
      href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css"
      integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm"
      crossorigin="anonymous"
    />
  </head>

  <body>
    <div class="row no-gutters">
      <div class="col-md-4 no-gutters">
        <div class="leftside d-flex justify-content-center align-items-center">
          <CreatePoll
            v-bind:is="CreatePoll"
            @onChangeQuestion="onChangeQuestion"
            @onChangeAnswers="onChangeAnswers"
          ></CreatePoll>
        </div>
      </div>
      <div class="col-md-4 no-gutters">
        <div
          class="centreside d-flex justify-content-center align-items-center"
        >
          <VotePoll
            :question="question"
            :answers="answers"
            @onChangeVote="onChangeVote"
          ></VotePoll>
        </div>
      </div>
      <div class="col-md-4 no-gutters ">
        <div class="rightside d-flex justify-content-center align-items-center">
          -
          <PollCharts :vote="vote" ref="pollCharts"></PollCharts>
        </div>
      </div>
    </div>
  </body>
</template>
<script>
import CreatePoll from "./CreatePoll.vue";
import VotePoll from "./VotePoll.vue";
import PollCharts from "./PollCharts.vue";

export default {
  components: {
    CreatePoll,
    VotePoll,
    PollCharts,
  },
  methods: {
    onChangeQuestion(value) {
      this.question = value;
    },
    onChangeAnswers(value) {
      this.answers = value;
    },
    onChangeVote(value) {
      this.vote = value;
      this.$refs.pollCharts.updatePollChart(this.vote);
    },
  },
  data() {
    return {
      question: "",
      answers: [],
      vote: {},
    };
  },
};
</script>
<style scoped>
.leftside,
.centreside,
.rightside {
  height: 50vh;
  width: 100%;
  border-style: solid;
}
@media screen and (min-width: 768px) {
  .leftside,
  .centreside,
  .rightside {
    height: 100vh;
  }
}
</style>
