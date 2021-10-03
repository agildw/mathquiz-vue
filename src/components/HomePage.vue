<template>
  <v-container fill-height>
    <v-row align-content="center" align="center" justify="center">
      <v-col>
        <v-card elevation="7" width="461" height="440">
          <v-card-title>Soal</v-card-title>
          <v-card-text>
            {{ soalNya }}
            <v-text-field
              placeholder="Jawab"
              v-model.lazy="inputAnswer"
            ></v-text-field>
          </v-card-text>
          <v-card-actions>
            <v-btn @click="submitAnswer()">Submit</v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
      <v-col>
        <v-card elevation="7" width="461" height="440">
          <v-card-title>Hasil</v-card-title>
          <v-card-text>
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
      inputAnswer: null,
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
      this.soalNya = this.firstNumber + this.operatorNya + this.secondNumber;
      this.hasilnya = eval(this.soalNya);
    },
    submitAnswer() {
      console.log(this.isCorrect);
      if (this.inputAnswer == this.hasilnya) {
        this.isCorrect = true;
        console.log(this.isCorrect);
        console.log(this.inputAnswer);
        console.log(this.hasilnya);
      } else {
        this.isCorrect = false;
        // console.log(this.isCorrect);
      }
    },
  },
  created() {
    this.randomin();
    this.resultMath();
  },
};
</script>