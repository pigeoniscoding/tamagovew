<template>
  <div class="home">
    <PetVue />
  </div>
</template>

<script>
// @ is an alias to /src
import PetVue from "@/components/PetVue.vue";

export default {
  name: "HomeView",
  components: {
    PetVue,
  },
};
</script>
