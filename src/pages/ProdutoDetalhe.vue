<template>
  <div class="produto-detalhe">
    <Header />
    <main>
      <Detalhe
        :title="viewDetalhe.title"
        :price="viewDetalhe.price"
        :img="viewDetalhe.img"
        :_id="viewDetalhe.id"      
      />
    </main>
    <Footer />
  </div>
</template>
<script>
import Header from "../components/Header.vue";
import Detalhe from "../components/Detalhe.vue";
import Footer from "../components/Footer.vue";

export default {
  name : "ProdutoDetalhe",
  components : {
    Header,
    Detalhe,
    Footer,  
  },
  data:function(){
    return{
      viewDetalhe: {},
    }
  },
  methods: {
    getProdutodetalhe: async function(){
    const result = await fetch("http://localhost:3000/produtos/" + this.$route.params.id)
    .then((res) => res.json())
    .catch((error) => {
      return {
        error:true,
        message:error,
      }
    })    
    if (!result.error){
      this.viewDetalhe = result;
    }
  }, 
  },  
  created: function() {
    this.getProdutodetalhe();
  },
    
  };
  
</script>
<style>
  
</style>