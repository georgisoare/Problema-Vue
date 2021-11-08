<template>
  <h3>
    Introduceți un șir de numere cuprinse între 100 și 999 separate prin virgulă
  </h3>
  <input type="text" v-model="numberInput" />
  <button @click="calculate">Calculează</button>

  <Max v-if="isClicked" :maxValues="maxValues" />

  <Modulo v-if="isClicked" :modulo="modulo" />

  <Matrix v-if="isClicked" :matrix="matrix" :modulo="modulo" />
</template>

<script>
import Max from "./Max.vue";
import Modulo from "./Modulo.vue";
import Matrix from "./Matrix.vue";

export default {
  name: "Content",
  components: { Max, Modulo, Matrix },

  data() {
    return {
      numberInput: "",
      numbers: [],
      maxValues: [],
      modulo: [],
      isClicked: false,
      matrix: [],
    };
  },
  methods: {
    calculate() {
      this.modulo = [];
      this.isClicked = true;

      try {
        this.numbers = this.getInputArray(this.numberInput);
        this.maxValues = this.getMaxValues(this.numbers);
        this.modulo = this.getModuloList(this.maxValues);
        this.matrix = this.initializeMatrix();
      } catch (e) {
        console.log(e);
      }
    },

    initializeMatrix() {
      return Array(4)
        .fill()
        .map(() => Array(4).fill("?"));
    },

    getMaxValues(values) {
      const maxValues = [];
      const maxMap = new Map();
      for (let i = 1; i < 10; i++) {
        maxMap.set(i, 0);
      }

      values.forEach((n) => {
        const firstDigit = Math.floor(n / 100);
        if (maxMap.get(firstDigit) < n) {
          maxMap.set(firstDigit, n);
        }
      });

      for (let value of maxMap.values()) {
        if (value !== 0) {
          maxValues.push(value);
        }
      }
      return maxValues;
    },

    getInputArray(numbersInput) {
      return numbersInput.split(",").map((s) => s.trim());
    },

    getModuloList(values) {
      return values.map((val) => String.fromCharCode(65 + (val % 26)));
    },
  },
};
</script>

<style src="../style.css"></style>
