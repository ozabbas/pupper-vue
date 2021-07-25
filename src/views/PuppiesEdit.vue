<template>
  <div class="home">
    <!-- <p>{{ editPuppyParams }}</p> -->
    Name: <input type="text" v-model="editPuppyParams.name">
    Age: <input type="text" v-model="editPuppyParams.age">
    Breed: <input type="text" v-model="editPuppyParams.breed">
    <p><button v-on:click="updatePuppy()">Update Puppy</button></p>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Welcome to the edit page!",
      editPuppyParams: {},
    };
  },
  created: function () {
    this.puppiesShow();
  },
  methods: {
    puppiesShow: function () {
      console.log("showing a puppy");
      axios
        .get(`http://localhost:3000/puppies/${this.$route.params.id}`)
        .then((response) => {
          console.log(response.data);
          this.editPuppyParams = response.data;
        });
    },
    updatePuppy: function () {
      console.log("updating puppy");
      // take all the params, send them to rails
      axios
        .patch(
          `http://localhost:3000/puppies/${this.$route.params.id}`,
          this.editPuppyParams
        )
        .then((response) => {
          console.log(response.data);
          this.$router.push("/puppies");
        });
    },
  },
};
</script>