<script setup>

import {ref} from "vue";
import InputField from "./InputField.vue";
import LovelyFrame from "./LovelyFrame.vue";

const name = ref('Mari')
const numOfRows = ref(10)
const numOfCols = ref(10)
const rowToHighlight = ref(1)
const colToHighlight = ref(10)
const showTheMath = ref(false)
</script>


<template>
  <section class="container">
    <h1> Multiplication Table </h1>
    <h2 v-if="name">Welcome {{ name }}!</h2>
    <h2 v-else>Please tell us your name</h2>

    <div class="inputs">

      <input-field label-text="What's your name?" v-model="name"/>

      <input-field label-text="How many rows do you want?" input-type="number" v-model="numOfRows"/>
      <input-field label-text="How many columns do you want?" input-type="number" v-model="numOfCols"/>
      <input-field label-text="Which row to highlight?" input-type="number" v-model="rowToHighlight"/>
      <input-field label-text="Which column to highlight?" input-type="number" v-model="colToHighlight"/>
      <input-field label-text="Show the math?" input-type="checkbox" v-model="showTheMath"/>

    </div>

    <lovely-frame>

    <table>
      <tr v-for="row in numOfRows" :class="{ highlight : row === rowToHighlight }">

        <td v-for="col in numOfCols" :class="{ highlight : col === 5 }">
          {{ row * col }}
        </td>

      </tr>
    </table>
    </lovely-frame>
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