<template>
<div id="app">
  <h3>掲示板に投稿する</h3>
  <label for="name">ニックネーム:</label>
  <input 
  id="name"
  type="text"
  v-model="name"
  >
  <br><br>
  <label for="comment">コメント:</label>
  <textarea 
    id="comment"
    v-model="comment"
  ></textarea>
  <br><br>
  <button @click="createComment">コメントをサーバーに送る</button>
  <h2>掲示板</h2>
</div>
</template>

<script>
import axios from "axios";
export default {
  data(){
    return {
      name: "",
      comment: ""
    };
  },
  methods: {
    createComment() {
      axios.post(
        'https://kaitotamura.github.io/vuejs-http/',
         {
             name: this.name,
             comment: this.comment
         })
        .then(response => {
          console.log(response);
        })
        .catch(error => {
          console.log(error);
        });
        this.name="";
        this.comment="";
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
