<template>
<div class="m">
  <h1>Settings for {{showName}}</h1>
  <p>
    <label>Username: </label><input type="text" v-model="username"><br>
    <button v-on:click="save">Save changes</button>
  </p>
</div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  name: "Settings",
  computed: {
    ...mapGetters(["showName"])
  },
  data() {
    return {
      // used to hold new username
      username: ""
    };
  },
  methods: {
    ...mapActions(["changeDisplayName", "updateDBName"]),
    save: function() {
      this.changeDisplayName(this.username);
      this.username = "";
      this.updateDBName();
    }
  }
};
</script>

<style>
button {
  margin: 20px 0;
}

p {
  text-align: left;
}
</style>
