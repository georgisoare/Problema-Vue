<template>
  <div class="content">
    <p>Matrix:</p>
    <table>
      <tr v-for="(row, i) in matrix" :key="row">
        <td v-for="(item, j) in row" :key="item" @click="changeItem(i, j)">
          {{ item }}
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  props: ["matrix", "modulo"],

  methods: {
    changeItem(i, j) {
      const moduloSet = new Set(this.modulo);
      this.matrix[i][j] = this.getRandomChar(moduloSet);
    },

    getRandomChar(moduloSet) {
      return Array.from(moduloSet)[Math.floor(Math.random() * moduloSet.size)];
    },
  },
};
</script>
