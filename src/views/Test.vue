<template>
  <div class="test">
    <h1>{{ message }}</h1>
    <button v-on:click="fireSweetAlert()">Test</button>
    <button v-on:click="fireSweetAlert2()">Test Two</button>
  </div>
</template>

<style>
.swal-overlay {
  background-color: rgba(43, 165, 137, 0.45);
}
</style>

<script>
import swal from "sweetalert";
export default {
  data: function () {
    return {
      message: "Welcome to Pokeworld!",
    };
  },
  created: function () {},
  methods: {
    fireSweetAlert: function () {
      swal("A wild Pikachu appeared! What do you want to do?", {
        buttons: {
          cancel: "Run away!",
          catch: {
            text: "Throw Pokéball!",
            value: "catch",
          },
          defeat: true,
        },
      }).then((value) => {
        switch (value) {
          case "defeat":
            swal("Pikachu fainted! You gained 500 XP!");
            break;

          case "catch":
            swal("Gotcha!", "Pikachu was caught!", "success");
            break;

          default:
            swal("Got away safely!");
        }
      });
    },
    fireSweetAlert2: function () {
      swal({
        title: "Here's a title!",
      });
    },
  },
};
</script>
