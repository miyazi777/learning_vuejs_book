<template>
  <section class="container">
    <h1>{{title}}</h1>
    <p>{{$store.state.message}}</p>
    <hr>
    <div class="link" @click="$store.commit({type:'count', message: 'add 1', add:1})">
      <a>clicked(+1): {{ $store.state.counter }}</a>
    </div>
    <div class="link" @click="$store.commit({type:'count', message: 'add 2', add:2})">
      <a>clicked(+2): {{ $store.state.counter }}</a>
    </div>
    <div class="link" @click="$store.commit('reset')">
      <a>reset</a>
    </div>
  </section>
</template>

<script>
export default {
  data: function() {
    return {
      title: 'Hello',
    };
  }
};
</script>

<style>
.container {
  padding: 5px 10px;
}
h1 {
  font-size: 60pt;
  color: #345980;
}
p {
  padding-top: 5px;
  font-size: 20pt;
}
pre {
  padding: 10px;
  font-size: 18pt;
  background-color: #efefef;
}
hr {
  margin: 10px 0px;
}
</style>
