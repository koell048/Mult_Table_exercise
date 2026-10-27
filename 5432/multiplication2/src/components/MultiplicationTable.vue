<script setup>

import {ref} from "vue";

const name = ref('Mari')
const numOfRows = ref(10)
const numOfCols = ref(10)
const rowToHighlight = ref(1)
const colToHighlight = ref(1)
</script>


<template>
  <section class="container">
    <h1> Multiplication Table </h1>
    <h2 v-if="name">Welcome {{ name }}!</h2>
    <h2 v-else>Please tell us your name</h2>

    <div class="inputs">

      <label>
        Name: <input type="text" v-model="name"/>
      </label>

      <label>
        How many rows do you want?
        <input type="number" v-model.number="numOfRows"/>
      </label>

      <label>
        How many columns do you want?
        <input type="number" v-model.number="numOfCols"/>
      </label>

    </div>

    <table>
      <tr v-for="row in numOfRows" :class="{ highlight : row === rowToHighlight }">

        <td v-for="col in numOfCols" :class="{ highlight : col === 5 }">
          {{ row * col}}
        </td>

      </tr>
    </table>
  </section>


</template>


<style scoped>
table {
  border: 4px solid black;

  tr {
    &.highlight {
      background-color: lightskyblue;
      color: white;
    }
    td {
      border: 1px dotted red;

      &.highlight {
        background-color: lightskyblue;
        color: white;
      }
    }
  }
}

section.container {
  border: 4px solid black;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;

  h1, h2, h3, h4, h5, h6 {
    margin: 0;
  }

  div.inputs {
    border: 2px solid red;
    gap: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;

    label {
      display: flex;
      border: 1px solid black;
      justify-content: space-between;
      width: 100%;
    }
  }
}

</style>