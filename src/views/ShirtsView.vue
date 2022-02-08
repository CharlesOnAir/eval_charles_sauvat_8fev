<template>
  <div style="text-align: center;">
    <h1>Liste des tee-shirts</h1>
    <a v-if="!liste_produits_count" :href="new_page">Aller à la page suivante</a>
    <a v-else :href="new_page">Aller à la page précédente</a>
  </div>
  <div v-if="!liste_produits_count" style="margin-top: 2em; display: grid;grid-template-columns: repeat(3, 1fr);">
    <div v-for="produit in liste_produits" style="background-color: white; padding: 30px; width: 269px; border-radius: 10px; margin-top: 10px;">
    <a :href="'/tee_shirt/' + produit.id">
      <img style="width: 200px;" :src="produit.imageURL" />
      <div style="display: flex; justify-content: space-between;">
        <h2 style="white-space: nowrap; overflow: hidden; text-overflow: ellipsis;">{{ produit.name }}</h2>
        <h1 v-if="produit.flag == 'NEW'" style="color: white; background-color: #02c8eb; width: 52px; border-radius: 50px; font-size: 15px; padding: 10px;">{{ produit.flag }}</h1>
        <h1 v-if="produit.flag == 'Sale!'" style="color: white; background-color: red; width: 52px; border-radius: 50px; font-size: 15px; padding: 10px;">{{ produit.flag }}</h1>
      </div>
      <h6>{{ produit.price }}</h6>
      </a>
    </div>
  </div>
  <div v-else style="text-align: center; margin-top: 5em;">
    <h2>Plus de produits disponibles</h2>
  </div>
</template>

<style>
</style>

<script>
import ax from 'axios'
export default {
    data() {
        var new_page = parseInt(this.$route.params.page) + 1;
        return {
          liste_produits: null,
          liste_produits_count: false,
          new_page: new_page
        }
    },
    mounted() {
      let self = this
      ax
        .get('http://vps-a47222b1.vps.ovh.net/TShirt/page/' + this.new_page)
        .then(function (response) {
          console.log(response);
          self.liste_produits = response.data
          if (self.liste_produits.length == 0) {
            self.liste_produits_count = true;
            self.new_page = self.new_page - 2;
          }
        })
    }
}
</script>
