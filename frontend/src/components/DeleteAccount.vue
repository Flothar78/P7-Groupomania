<template>
  <v-btn
    elevation="1"
    class="mb-8 mt-12 mx-3"
    color="indigo lighten-1"
    text
    @click="deleteAccount"
  >
    Supprimer votre compte
  </v-btn>
</template>

<script>
import axios from "axios";
export default {
  name: "deleteAccount",
  data() {
    return {
      user: {},
    };
  },
  methods: {
    deleteAccount() {
      if (confirm("Etes-vous certain de vouloir supprimer votre compte ?")) {
        axios
          .delete("http://localhost:3000/users", {
            headers: {
              Authorization: "Bearer" + " " + this.$store.state.token,
            },
          })
          .catch((error) => error.status(401).json(error));
      }
    },
  },
};
</script>
