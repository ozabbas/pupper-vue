<template>
  <div class="puppies-new">
    <h1>Make a new puppy</h1>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      newPuppiesParams: {},
      errors: [],
    };
  },
  methods: {
    submit: function () {
      axios
        .post("/puppies", this.newPuppiesParams)
        .then((response) => {
          console.log(response.data);
          this.$router.push("/puppies");
        })
        .catch((error) => {
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>