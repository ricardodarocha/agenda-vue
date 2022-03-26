<template>
  <div class="hello">
    <h1>{{ dataformatadastr }}</h1>

    <button @click="i -= passo">
      <i class="uil uil-angle-left-b"></i>
    </button>

    <button @click="i += passo">
      <i class="uil uil-angle-right-b"></i>
    </button>

    <button @click="selecionarhoje()">
      Hoje
    </button>

    <button @click="i = 0">
      <i class="uil uil-calendar-alt"></i>
    </button>

    <button @click="agendar">
      <i class="uil uil-schedule"></i>Agendar
    </button>

    <button @click="passo = 1">Dia</button>

    <button @click="passo = 7">Semana</button>

    <button @click="passo = 30">Mês</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: function () {
    return {
      i: 0,
      passo: 1
    }
  },
  computed: {
    dataformatadastr() {
      let _data = new Date();
      _data.setDate(_data.getDate() + this.i);
      return this.dataformatada(_data)
    }
  },
  methods: {
    agendar: function () {
      console.log('agendou')
    },
    dataformatada: function (date) {
      let dia = date.getDate();
      let mes = ['janeiro',
        'fevereiro',
        'março',
        'abril',
        'maio',
        'junho',
        'julho',
        'agosto',
        'setembro',
        'outubro',
        'novembro',
        'dezembro'][date.getMonth()]
      let ano = date.getFullYear()

      return this.passo == 30 ? `${mes} de ${ano}` : `${dia} de ${mes} de ${ano}`
    },
    selecionarhoje: function () {
      this.i = 0;
    },
  },
  props: {
    msg: String
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
