<template>
  <section class="container">
    <h1>{{ title }}</h1>
    <p>{{ message }}</p>
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
      msg: '',
      message: 'axios sample',
    };
  },
  asyncData: async function() {
    let id = 1;
    let result = await axios.get(url + id);
    return { json_data: result.data }
  },
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
