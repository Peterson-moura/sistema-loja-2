<template>
  <div class="pedidos">
    <Header></Header>
    <div class="container">
      <div class="row">
        <div  class="col-md-12">
          <div class="box" v-for="pedido in pedidos" :key="pedido._id">
          <p>Id do Produto:{{ pedido.produtoId }}</p>
          <p>CPF Cliente: {{ pedido.clienteCPF }}</p>
          <p>Valor Unitário: {{ pedido.valorUnitario }}</p>
          <p>Valor Total: {{ pedido.ValorTotal }}</p>
          <p>Quantidade: {{ pedido.quantidade }}</p>
        </div>
        </div>        

      </div>
    </div>
    <Footer></Footer>
  </div>
</template>
<script>
import Header from "../components/Header.vue";
import Footer from "../components/Footer.vue";

export default {
  name: "Pedidos",
  components: {
    Header,
    Footer,
  },
  props: {},
  data: function () {
    return {
      pedidos: [],
      produtoId: "",
      valorTotal: "",
      valorUnitatio: "",
      quantidade: "",
      clienteCPF: "",
    };
  },

  methods: {
    getPedido: async function () {
      const result = await fetch("http://localhost:3000/pedidos")
        .then((res) => {
          return res.json();
        })
        .catch((error) => {
          return {
            error: true,
            message: error,
          };
        });
      if (!result.error) {
        this.pedidos = result;
      }
    },
  },
  created: function () {
    this.getPedido();
  },
};
</script>
<style>
.box {
  width: 50%; 
  background: #DCDCDC;
}


</style>