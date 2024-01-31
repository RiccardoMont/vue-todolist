<script>
export default {
  name: 'App',
  data() {
    return {
      newElement: {
        showElement: true,
        text: '',
        done: false
      },
      emptyCase: false,
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

      this.spesa[index].done = !this.spesa[index].done;
      console.log('ecco');

    },
    mostrare(index) {

      if (this.spesa[index].showElement) {

        this.spesa[index].showElement = false;

      }
    },
    add() {

      if (this.newElement.text.trim().length === 0) {

        this.emptyCase = true;
        console.log("The string is empty");

      } else {

        this.emptyCase = false;
        const newObj = { ...this.newElement };
        this.spesa.push(newObj);
        this.newElement.text = '';

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
      <li v-for="(elemento, index) in spesa" :class="!elemento.done ? '' : 'marked'" v-show="elemento.showElement" @click="smarcare(index)"><input
          type="checkbox" v-model="elemento.done"> {{ elemento.text }}
        <font-awesome-icon class="red" icon="fa-solid fa-x" @click="mostrare(index)" />
      </li>
    </ul>
    <br>
    <div id="adding">
      <input @keyup.enter="add" type="text" id="newItem" v-model="newElement.text">
      <button @click="add">Aggiungi</button>
    </div>
    <p v-show="emptyCase">Inserire del testo valido</p>
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

#adding {
  display: flex;
  justify-content: space-between;
}

#newItem {
  border-radius: 8px;
  border: 1px solid rgb(96, 96, 96);
  padding: 0.6em 1.2em;
  font-size: 1em;
  font-weight: 500;
}

p {
  color: red;
  text-align: start;
}
</style>
