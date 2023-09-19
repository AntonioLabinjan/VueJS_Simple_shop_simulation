<template>
  <div id="app">
    <center><h1>Simulacija trgovine</h1></center>
    <PostavljanjeNovca @unos-novca="postaviNovac" :novac="novac" />
    <UnosProizvoda :novac="novac" @update:novac="postaviNovac" @dodaj-kupovinu="dodajKupovinu" />
    <TrenutnaKupovina :trenutna-kupovina="trenutnaKupovina" />
  </div>
</template>

<script>
import PostavljanjeNovca from "./components/PostavljanjeNovca.vue";
import UnosProizvoda from "./components/UnosProizvoda.vue";
import TrenutnaKupovina from "./components/TrenutnaKupovina.vue";

export default {
  components: {
    PostavljanjeNovca,
    UnosProizvoda,
    TrenutnaKupovina
  },
  data() {
    return {
      novac: 0,
      trenutnaKupovina: []
    };
  },
  methods: {
    postaviNovac(novac) {
      this.novac = novac;
    },
    dodajKupovinu(novaKupovina) {
      this.trenutnaKupovina.push(novaKupovina);
    }
  }
};
</script>
