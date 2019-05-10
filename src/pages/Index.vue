<template>
  <q-page class="flex flex-center q-ma-md">
    <!-- <iframe id="iframe"
      :src="src"
      style="position: absolute; width:100%; height: 80%; border: none">
    </iframe> -->
     <div class="shadow-5" style="max-width: 500px; margin: auto">
      <div class="text-white text-center bg-green" style="min-height:40px; padding:10px;">
        <span class="q-title q-ma-md">RESULTADO DE EXAMES</span>
      </div>
      <form action="https://www.pulsesaude.com.br/Autenticacao/Labnet" method="post" name="formulario" target="_self" enctype="multipart/form-data" autocomplete="off" style="padding: 30px">
        <div class="row gutter-sm">
          <div class="col-12">
            <p class="text-center"><img src="statics/logo.gif"></p>
          </div>
          <div class="col-12">
            <p class="text-center"><b>Entre com o seu localizador e senha</b></p>
          </div>
          <div class="col-12">
            <!-- <q-input id="cad_localizador" name="Localizador" type="text" size="12" maxlength="20" /><br> -->
            <q-input
              ref="localizador"
              v-model="Localizador"
              type="text"
              stack-label="Localizador"
              :max-height="20"
              name="Localizador"
             />
          </div>
          <div class="col-12">
            <!-- CPF ou Chave:<br> -->
            <!-- <q-input id="Text1" placeholder="Digite seu CPF ou Chave" name="Confirmador" type="text" size="12" maxlength="20"/> -->
            <q-input
              v-model="Text1"
              type="Confirmador"
              stack-label="Senha"
              :max-height="20"
              name="Confirmador"
             />
          </div>
        </div>
        <br>
        <!-- P407187238613 0109-->
        <q-btn type="submit" class="float-right q-ma-md" color="green" icon="done" label="ACESSAR"/>
        <!-- <q-btn class="float-right q-ma-md" color="green" icon="done" label="JAJA" @click="logar"/> -->
      </form>
    </div>
  </q-page>
</template>

<style>
</style>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      Localizador: '',
      Confirmador: '',
      src: 'src'
    }
  },
  mounted: function () {
    // this.logar()
    this.$refs.localizador.focus()
  },
  methods: {
    logar () {
      // this.src = 'https://www.pulsesaude.com.br/Autenticacao/Labnet'
      this.$axios.post('https://www.pulsesaude.com.br/Autenticacao/Labnet', {
        Localizador: this.Localizador,
        Confirmador: this.Confirmador
      })
        .then(response => {
          console.log(response.data)
        })
        .catch(e => {
          this.erros.push(e)
        })
    }
  }
}
</script>
