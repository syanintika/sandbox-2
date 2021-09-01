<template>
  <div>
    <h4>Belajar Watcher</h4>
    <input type="text" class="form-control" v-model="question">
    <h5>{{answer}}</h5>
    <img :src="img" class="w-100" alt="" srcset="">
  </div>
</template>
<script>
export default {
  data() {
    return {
      img: "",
      question: "",
      answer: "hhmmmm.... apa ya?",
    };
  },
  watch: {
    question(newValue, oldValue) {
      if (newValue.indexOf("?") > -1) {
        this.getAnswer();
      }
    },
  },
  methods: {
    getAnswer() {
      this.answer = "....bentar masih mikir";
      this.$axios.$get("https://yesno.wtf/api").then((response) => {
        console.log(response);
        this.answer = response.answer;
        this.img = response.image;
      });
    },
  },
};
</script>