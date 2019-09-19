<template>
  <section class="container">
    <h1>{{ title }}</h1>
    <p>{{ message }}</p>
    <div>
      <input type="text" v-model="msg"/>
      <button @click="doClick">click</button>
    </div>
    <table>
      <tr>
        <th>User ID</th>
        <td>{{json_data.userId}}</td>
      </tr>
      <tr>
        <th>ID</th>
        <td>{{json_data.id}}</td>
      </tr>
      <tr>
        <th>Title</th>
        <td>{{json_data.title}}</td>
      </tr>
      <tr>
        <th>Body</th>
        <td>{{json_data.body}}</td>
      </tr>
    </table>
  </section>
</template>

<script>
const axios = require('axios');

let url = "https://jsonplaceholder.typicode.com/posts/";

export default {
  data: function() {
    return {
      title: 'Axios',
      message: 'axios sample',
      msg: '',
      json_data: {},
    };
  },
  methods: {
    doClick: function(event) {
      axios.get(url + this.msg).then((res) => {
        this.message = 'get ID=' + this.msg;
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
