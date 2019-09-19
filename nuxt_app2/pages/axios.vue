<template>
  <section class="container">
    <h1>{{ title }}</h1>
    <p>{{ message }}</p>
    <input v-model="find">
    <button @click="getData">Click</button>
    <hr>
    <ul>
      <li>{{json_data}}</li>
    </ul>
  </section>
</template>

<script>
const axios = require('axios');

let url = "https://takeshi-learn-vue-js.firebaseio.com/person/";

export default {
  data: function() {
    return {
      title: 'Axios',
      find: '',
      message: 'axios sample',
      json_data: {},
    };
  },
  methods: {
    getData: function() {
      let id_url = url + this.find + '.json';
      axios.get(id_url).then((res) => {
        this.message = 'get ID = ' + this.find;
        this.json_data = res.data;
      }).catch((error) => {
        this.message = 'ERROR';
        this.json_data = {};
      });
    }
  }
}
</script>

<style>
ul {
  margin: 0px 10px;
  background-color: aliceblue;
}
li {
  padding: 10px;
  font-size: 16pt;
}
tr th {
  width: 150px;
  background-color: darkblue;
  color: white;
  font-size: 16pt;
}
tr td {
  padding: 5px 10px;
  background-color: #eef;
  font-size: 14pt;
}
</style>
