<template>
  <div>
    <h2>Unesi novi proizvod</h2>
    <input v-model="noviProizvod.naziv" placeholder="Naziv proizvoda">
    <input v-model.number="noviProizvod.cijena" placeholder="Cijena po komadu">
    <input v-model.number="noviProizvod.kolicina" placeholder="Broj komada">
    <button @click="dodajProizvod">Dodaj proizvod</button>
    
    <h2>Proizvodi za kupovinu</h2>
    <ul>
      <li v-for="(proizvod, index) in proizvodi" :key="index">
        {{ proizvod.naziv }} - {{ proizvod.cijena }} kn po komadu (Dostupno: {{ proizvod.kolicina }})
        <input v-model.number="kolicinaProizvoda[index]" placeholder="Količina za kupovinu">
        <button @click="kupiProizvod(index)">Kupi</button>
      </li>
    </ul>
    
    <p>Raspoloživi novac: {{ novac }} kn</p>
  </div>
</template>

<script>
export default {
  name: "UnosProizvoda",
  props: {
    novac: Number,
    trenutnaKupovina: Array
  },
  data() {
    return {
      noviProizvod: {
        naziv: "",
        cijena: 0,
        kolicina: 0
      },
      proizvodi: [],
      kolicinaProizvoda: []
    };
  },
  methods: {
    dodajProizvod() {
      if (this.noviProizvod.naziv && this.noviProizvod.cijena > 0 && this.noviProizvod.kolicina > 0) {
        this.proizvodi.push({ ...this.noviProizvod });
        this.kolicinaProizvoda.push(0);
        this.noviProizvod = { naziv: "", cijena: 0, kolicina: 0 }; 
      }
    },
    kupiProizvod(index) {
      const proizvod = this.proizvodi[index];
      const kolicina = this.kolicinaProizvoda[index];
      if (proizvod && proizvod.kolicina >= kolicina && this.novac >= proizvod.cijena * kolicina) {
        this.proizvodi[index].kolicina -= kolicina;
        const ukupnaCijenaKupovine = proizvod.cijena * kolicina;
        const novaKupovina = {
          proizvod: proizvod,
          kolicina: kolicina,
          ukupnaCijena: ukupnaCijenaKupovine
        };
        this.$emit("update:novac", this.novac - ukupnaCijenaKupovine);
        this.$emit("dodaj-kupovinu", novaKupovina); 
      }
    }
  }
};
</script>
