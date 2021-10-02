<template>
  <v-container fill-height>
    <v-row align-content="center" align="center" justify="center">
      <v-col>
        <v-card elevation="2" width="461" height="440">
          <v-card-title>Soal</v-card-title>
          <v-card-text>
            {{ soalNya }}
          </v-card-text>
        </v-card>
      </v-col>
      <v-col>
        <v-card elevation="2" width="461" height="440">
          <v-card-title>Hasil</v-card-title>
          <v-card-text>
            {{ hasilnya }}
          </v-card-text>
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
  },
  created() {
    this.randomin();
    this.resultMath();
  },
};
</script>