<template>
  <section class="produtos">
    <div class="container">
      <div class="row">
        <div class="col-md-6">
          <h2>Produtos</h2>
        </div>
        <div class="col-md-6">
          <input type="text" placeholder="Pesquisar.." v-model="search" />
        </div>
      </div>
      <div class="row">
        <div v-for="prod in productsFiltered" :key="prod.id" class="col-md-4">
          <Card 
            :title="prod.title"
            :price="prod.price"
            :img="prod.img"
          />
        </div>
      </div>
    </div>
  </section>
</template>
<script>
import Card from "./Card.vue";

export default {
  name : "Produtos",
  components : {
    Card
  },
  data : function(){
    return {
      search : "",
      produtos : [
        {
          id : 1,
          title : "Red Dead Redemption II",
          price : "100,00",
          img : require('../assets/red-read.jpg'),
        },
        {
          id: 2,
          title : "Dshonored 2",
          price : "89,90,",
          img : require('../assets/dishonored.jpg'),
        },
        {
          id : 3,
          title : "Assassin's Creed Odyssey",
          price : "129.90",
          img : require('../assets/ACOdyssey.jpg'),
        },
        {
          id : 4,
          title : "Red Dead Redemption II",
          price : "100,00",
          img : require('../assets/red-read.jpg'),
        },
        {
          id: 5,
          title : "Dshonored 2",
          price : "89,90,",
          img : require('../assets/dishonored.jpg'),
        },
        {
          id : 6,
          title : "Assassin's Creed Odyssey",
          price : "129,90",
          img : require('../assets/ACOdyssey.jpg'),
        },

      ]
    }
  },
  computed: {
    productsFiltered : function() {
      return this.produtos.filter((event) =>
        event.title.toLowerCase().indexOf(this.search.toLowerCase()) > -1 
      )
    }
  }
}
</script>
<style>
  .produtos{
    padding: 56px 0px;
    background-color: #E2E2E2;
    width: 100%;
    min-height : 800px;
  } 

  .produtos .row{
    align-items: flex-start;
  }

  .produtos h2{
    font-size : 36px;
    color: #ae382b;
    padding: 0;
    margin : 0;
  } 

  .produtos input {
    border-radius : 50px;
    background-color: #f1f1f1;
    border: none;
    width: 70%;
    height: 30px;
    padding: 4px 14px;
    float: right;    
  }
</style>