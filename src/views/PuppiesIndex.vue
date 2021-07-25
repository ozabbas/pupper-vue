<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <!-- <h1>{{ puppies }}</h1> -->
    <div v-for="puppy in puppies">
      <ul>
        <li>Id: {{ puppy.id }}</li>
        <li>Name: {{ puppy.name }}</li>        
        <a v-bind:href="`/puppies/${puppy.id}/edit`">Edit puppy</a>
        <hr />
      </ul>
      
    </div>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Puppies index action!",
      puppies: [],
    };
  },
  created: function () {
    this.getPuppies();
  },
  methods: {
    getPuppies: function () {
      console.log("getting puppies");
      axios.get("http://localhost:3000/puppies").then((response) => {
        console.log(response.data);
        this.puppies = response.data;
      });
    },
  },
};
</script>