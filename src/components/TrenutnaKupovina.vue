<template>
  <div>
    <h2>Trenutna kupovina</h2>
    <ul>
      <li v-for="(stavka, index) in trenutnaKupovina" :key="index">
        {{ stavka.proizvod.naziv }} x {{ stavka.kolicina }} - {{ stavka.proizvod.cijena }} kn po komadu = {{ stavka.ukupnaCijena }} kn
      </li>
    </ul>
    <p>Ukupno: {{ ukupnaCijenaKupovine }} kn</p>
  </div>
</template>

<script>
export default {
  name: "TrenutnaKupovina",
  props: {
    trenutnaKupovina: Array
  },
  computed: {
    ukupnaCijenaKupovine() {
      return this.trenutnaKupovina.reduce((total, stavka) => total + stavka.ukupnaCijena, 0);
    }
  }
};
</script>
