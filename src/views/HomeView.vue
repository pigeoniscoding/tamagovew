<script>
// @ is an alias to /src
import { reactive, toRefs } from "vue";
import DinoPet from "@/components/DinoPet.vue";
import PetVue from "@/components/PetVue.vue";

export default {
  name: "HomeView",
  components: {
    DinoPet,
    PetVue,
  },
  setup() {
    const state = reactive({
      petname: "",
      userinput: "",
      showCreatePetForm: true,
    });

    const createpet = () => {
      state.petname = state.userinput;
      state.showCreatePetForm = false;
    };

    return {
      ...toRefs(state),
      createpet,
    };
  },
};
</script>

<template>
  <div class="home">
    <h1>{{ petname }}</h1>
    <section :class="$style.wrapper">
      <PetVue />
      <DinoPet :class="$style.DinoPet" v-if="petname" />
    </section>
    <form v-if="showCreatePetForm" @submit.prevent>
      <label for="pet-name">pet name</label>
      <input type="text" id="pet-name" v-model="userinput" />
      <button @click="createpet">New Pet</button>
    </form>
  </div>
</template>

<style module>
.wrapper {
  position: relative;
}
.DinoPet {
  position: absolute;
  max-width: 120px;
  left: 610px;
  top: 220px;
}
</style>
