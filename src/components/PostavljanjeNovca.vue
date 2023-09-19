<template>
  <div>
    <h2>Unesi novčani iznos</h2>
    <input v-model.number="novac" placeholder="Novčani iznos">
    <button @click="potvrdiUnos">Potvrdi unos</button>
  </div>
</template>

<script>
export default {
  name: "PostavljanjeNovca",
  data() {
    return {
      novac: 0
    };
  },
  methods: {
    potvrdiUnos() {
      this.$emit("unos-novca", this.novac); 
    }
  }
};
</script>
