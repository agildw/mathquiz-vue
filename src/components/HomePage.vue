<template>
  <v-container fill-height>
    <v-row align-content="center" align="center" justify="center">
      <v-col>
        <v-card elevation="7" width="461" height="440">
          <v-card-title>Question</v-card-title>
          <v-card-text>
            {{ soalNya }}
            <v-text-field
              v-if="isCorrect != null"
              v-model="inputAnswer"
              disabled
            ></v-text-field>
            <v-text-field
              v-else
              type="number"
              placeholder="Answer"
              v-model.lazy="inputAnswer"
            ></v-text-field>
          </v-card-text>
          <v-card-actions>
            <v-btn
              @click="submitAnswer()"
              v-if="inputAnswer != ''"
              color="success"
              small
              >Submit</v-btn
            >
            <v-btn @click="submitAnswer()" disabled v-else color="success" small
              >Submit</v-btn
            >
            <v-btn
              small
              color="primary"
              @click="
                randomin();
                resultMath();
                isCorrect = null;
                inputAnswer = null;
              "
              ><v-icon>mdi-reload</v-icon></v-btn
            >
          </v-card-actions>
        </v-card>
      </v-col>
      <v-col>
        <v-card elevation="7" width="461" height="440">
          <v-card-title>Answer</v-card-title>
          <v-card-text v-if="isCorrect !== null">
            {{ hasilnya }}
          </v-card-text>
          <v-card-text v-if="isCorrect == true">Benar</v-card-text>
          <v-card-text v-else-if="isCorrect == false">salah</v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      firstNumber: null,
      secondNumber: null,
      operatorMath: ["+", "-", "*", "/"],
      operatorNya: null,
      soalNya: null,
      hasilnya: null,
      inputAnswer: "",
      isCorrect: null,
    };
  },
  methods: {
    randomin() {
      this.firstNumber = Math.floor(Math.random() * 101) + 1;
      this.secondNumber = Math.floor(Math.random() * 101) + 1;
      this.operatorNya =
        this.operatorMath[Math.floor(Math.random() * this.operatorMath.length)];
    },
    resultMath() {
      this.soalNya = `${this.firstNumber} ${this.operatorNya} ${this.secondNumber}`;
      this.hasilnya = eval(this.soalNya);
    },
    submitAnswer() {
      console.log(this.inputAnswer);
      if (this.inputAnswer == this.hasilnya) {
        this.isCorrect = true;
      } else {
        this.isCorrect = false;
      }
    },
  },
  created() {
    this.randomin();
    this.resultMath();
  },
};
</script>