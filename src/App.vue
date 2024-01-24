<script>
export default {
  name: 'App',
  data() {
    return {
      spesa: [
        {
          showElement: true,
          text: 'Pomodoro',
          done: false
        },
        {
          showElement: true,
          text: 'Peperoni',
          done: false
        },
        {
          showElement: true,
          text: 'Pollo',
          done: false
        },
        {
          showElement: true,
          text: 'Curry',
          done: false
        },
        {
          showElement: true,
          text: 'Paprika',
          done: false
        },
        {
          showElement: true,
          text: 'Aglio',
          done: false
        },
        {
          showElement: true,
          text: 'Olio',
          done: false
        },
        {
          showElement: true,
          text: 'Salsa di soia',
          done: false
        },
        {
          showElement: true,
          text: 'Latte di cocco',
          done: false
        },
        {
          showElement: true,
          text: 'Salvia',
          done: false
        },
        {
          showElement: true,
          text: 'Piadine',
          done: false
        }
      ]
    }
  },
  methods: {
    smarcare(index) {

      if (this.spesa[index].done === false) {

        this.spesa[index].done = true;

      } else {

        this.spesa[index].done = false;

      }

    },
    mostrare(index) {

      if (this.spesa[index].showElement === true) {

        this.spesa[index].showElement = false;

      }
    }
  }
}


</script>

<template>
  <div>
    <h1>Stasera devo fare il pollo al curry</h1>
    <h3>Lista della spesa:</h3>
    <ul>
      <li v-for="(elemento, index) in spesa" :class="elemento.done === false ? '' : 'marked'"
        v-show="elemento.showElement"><input type="checkbox" @change="smarcare(index)"> {{ elemento.text }}
        <font-awesome-icon class="red" icon="fa-solid fa-x" @click="mostrare(index)" /></li>
    </ul>

  </div>
</template>

<style>
ul {
  text-align: left;
  list-style: none;
}

.marked {
  text-decoration: line-through;
}

.red {
  color: red;
}
</style>
