<template>
  <div class="drinks">
    <h1>Страница со списком напитков и рейтингами</h1>

    <table class="drinks-list">
      <thead>
         <tr>
           <th>Название</th>
           <th>Описание</th>
           <th>Рейтинг</th>
         </tr>
      </thead>
      <tbody>
        <tr v-for="drink in drinks" v-bind:key="drink">
          <td>{{ drink.name }}</td>
          <td>{{ drink.description }}</td>
          <td>{{ drink.rating }}/10</td>
        </tr>
      </tbody>

    </table>
  </div>
</template>

<style>
.drinks-list {
   border: 1px solid black;
   margin-left: auto;
   margin-right: auto;
}
.drinks-list > td {
   text-align: center;
}
</style>

<script>
import axios from 'axios';

const BASE_API_URL = 'http://localhost:8080/api/v1';

export default {
  name: 'ListDrinks',
  components: {
  },
  methods: {
    getDrinks() {
      axios.get(`${BASE_API_URL}/drinks/`).then((response) => {
        this.drinks = response.data;
      });
    },
  },
  data() {
    return {
      drinks: {},
    };
  },
  mounted() {
    this.getDrinks();
  },
};
</script>
