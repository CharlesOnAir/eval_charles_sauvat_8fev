<template>
  <div style="text-align: center; display: flex; justify-content: space-between; align-items: center;">
    <img style="width: 200px;" :src="infoProduit.imageURL"/>
    <div style="text-align: left;">
        <H1>{{infoProduit.name}}</H1>
        <p>{{infoProduit.price}}</p>
        <p>{{infoProduit.description}}</p>
    </div>
  </div>
  
</template>

<style>
</style>

<script>
import ax from 'axios'
export default {
    data() {
        var id_produit = this.$route.params.id;
        return {
          id_produit: id_produit,
          infoProduit: ""
        }
    },
    mounted() {
      let self = this
      ax
        .get('http://vps-a47222b1.vps.ovh.net/TShirt/' + this.id_produit)
        .then(function (response) {
          self.infoProduit = response.data
        })
    }
}
</script>
