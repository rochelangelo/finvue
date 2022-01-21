<template>
  <div>
    <div>
        <form id="form-insert" @submit="add">
            <div class="input-form">
                <label for="reference">Referencia:</label>
                <input type="text" id="reference" name="reference" v-model="reference" placeholder="ref do gasto/receita" />
            </div>
            <div class="input-form">
                <label for="type">Tipo:</label>
                <select id="type" name="type" v-model="type">
                    <option value="">Selecione se é gasto ou receita</option>
                    <option v-for="type in types" :value="type" :key="type">{{type}}</option>
                </select>
            </div>
            <div class="input-form">
                <label for="category">Categoria:</label>
                <select v-if="type === 'gasto'" id="category" name="category" v-model="category">
                    <option value="">Selecione a categoria</option>
                    <option v-for="gasto in gastos" :value="gasto" :key="gasto">{{gasto}}</option>
                </select>
                <select v-if="type === 'receita'" id="category" name="category" v-model="category">
                    <option value="">Selecione a categoria</option>
                    <option v-for="receita in receitas" :value="receita" :key="receita">{{receita}}</option>
                </select>
            </div>

            <div class="input-form-dinheiro">
                <label for="value">Valor: R$</label>
                <input type="number" step="0.01" min="0" id="value" name="value" v-model="value" placeholder="Valor do gasto/receita" />
            </div>

            <div class="input-form">
                <input type="submit" class="submit-form" value="INCLUIR"/>
            </div>

        </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "FormInsert",
  data: () => ({
          types: ["gasto", "receita"],
          gastos: ["Mercado","Estudos","Imovel","Mecanico","Saude"],
          receitas: ["Salário","Freelancer","Poker"],
          reference: "",
          category: "",
          type: "",
          value: null,
  }),
  methods: {
      add(e){
          e.preventDefault();
          if(this.reference != "" || this.category != "" || this.type != "" || this.value != null){
              const newDado = {
                  id: Math.floor(Math.random() * 100),
                  reference: this.reference,
                  category: this.category,
                  type: this.type,
                  value: parseFloat(this.value)
              }
              if(newDado.type === "gasto"){
                  const valor = newDado.value
                  newDado.value = valor * -1
              }
              if(newDado.reference != " "){
                  this.$emit('add-item-event', newDado)
              }
              this.reference = "";
              this.category = "";
              this.type = "";
              this.value = "";
          }
      }
  }
};
</script>

<style scoped>
    #form-insert {
        max-width: 80vh;
        min-height: 60vh;
        margin: 0 auto;
        padding-top: 10vh;
        padding-bottom: 5vh;
    }

    .input-form{
        display: flex;
        flex-direction: column;
        margin-bottom: 15px;
    }

    .input-form-dinheiro{
        margin-bottom: 15px;
    }

    label{
        font-weight: bold;
        margin-bottom: 7px;
        padding: 5px 10px;
        color: #424242;
        border-left: 3px solid #01579B;
    }

    input, select {
        padding: 5px 10px;
        width: 60vh;
        margin: 2px solid #424242;
    }

    .submit-form{
        background-color: #FDD835;
        color: #424242;
        width: 20vh;
        font-weight: bold;
        border: 2px solid #424242;
        border-radius: 2vh;
        padding: 10px;
        font-size: 16px;
        margin: 0 auto;
        cursor: pointer;
        transition: .5s;
    }

    .submit-form:hover{
        background-color: #424242;
        color: #FDD835;
    }
</style>
