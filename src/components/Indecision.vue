<template>
  <img :src="bgImg" alt="bg" />
  <div class="bg-dark"></div>

  <div class="indecision-container">
    <input
      type="text"
      name=""
      id=""
      placeholder="hazme una pregunta"
      v-model="question"
    />
    <p>Recuerda terminar con un signo de interrogacion (?)</p>

    <div v-if="isValidQuestion">
      <h2>{{ question }}</h2>
      <h1>{{ answer }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: "Indecision",
  data() {
    return {
      question: null,
      answer: null,
      bgImg: null,
    };
  },
  methods: {
    async getAnswer() {
      this.answer = "Pensando...";

      fetch("https://yesno.wtf/api")
        .then((res) => res.json())
        .then((data) => {
          if (data.answer === "yes") this.answer = "Si";
          else if (data.answer === "no") this.answer = "No";
          else this.answer = "Tal vez";
          this.bgImg = data.image;
        })
        .catch((e) => {
          this.answer = "No se";
          this.bgImg = null;
        });
    },
  },
  computed: {
    isValidQuestion() {
      return typeof this.question === "string" && this.question.at(-1) === "?";
    },
  },
  watch: {
    question() {
      if (this.isValidQuestion) this.getAnswer();
    },
  },
};
</script>

<style scoped>
img,
.bg-dark {
  position: fixed;
  left: 0;
  top: 0;
  height: 100vh;
  width: 100vw;
  max-height: 100%;
  max-width: 100%;
}

.bg-dark {
  background-color: rgba(0, 0, 0, 0.4);
}

.indecision-container {
  position: relative;
  z-index: 99;
}

input {
  width: 250px;
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
}

input:focus {
  outline: none;
}

p {
  margin-top: 0;
  color: white;
  font-size: 20px;
}

h1,
h2 {
  color: white;
}

h2 {
  margin-top: 150px;
}
</style>
