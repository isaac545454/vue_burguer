<template>
  <div>
    <p>Component de mensagem</p>
    <div>
      <Form id="burguer-form">
        <div class="input-container">
          <label for="name"> Name dp cliente </label>
          <input
            type="text "
            id="name"
            v-model="name"
            placeholder="Digite seu Nome"
          />
        </div>
        <div class="input-container">
          <label for="bread"> Escolha o pão </label>
          <select id="bread" v-model="bread" placeholder="Digite seu Nome">
            <option value="">Selecione Seu Pão</option>
            <option v-for="b in bread" :key="b.id" value="p.tipo">
              {{ b.tipo }}
            </option>
          </select>
        </div>
        <div class="input-container">
          <label for="meat"> Escolha o Carne </label>
          <select id="meat" v-model="meat" placeholder="Digite seu Nome">
            <option value="">Selecione o Tipo de Carne</option>
            <option v-for="m in meat" :key="m.id" value="m.tipo">
              {{ m.tipo }}
            </option>
          </select>
        </div>
        <div class="optional-container">
          <label for="optional" id="optional-title">
            Escolha os Adicionais
          </label>
          <div id="checkbox-container" v-for="o in optional" :key="o.id">
            <input
              type="checkbox"
              name="optional"
              v-model="optional"
              :value="optional.tipo"
            />
            <span>{{ o.tipo }}</span>
          </div>
        </div>
        <div class="submit-btn">
          <input type="submit" class="submit-btn" value="criar meu Burguer" />
        </div>
      </Form>
    </div>
  </div>
</template>

<script>
import { Vue } from "vue-class-component";
export default class BurguerForm extends Vue {
  data() {
    return {
      optional: null,
      meat: null,
      bread: null,
      name: null,
      optionalUser: [],
      meatUser: null,
      breadUser: null,
      status: "Solicitado",
      msg: null,
    };
  }
  async getIngredients() {
    const res = await fetch("http://localhost:3000/ingredientes");
    const dataRes = await res.json();
    console.log(dataRes);
    this.bread = dataRes.paes;
    this.meat = dataRes.carnes;
    this.optional = dataRes.opcionais;
    console.log(this.meat);
  }
  mounted() {
    this.getIngredients();
  }
}
</script>

<style scoped>
#burguer-form {
  max-width: 400px;
  margin: 0 auto;
}
.input-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

label {
  font-weight: bold;
  color: #222;
  padding: 5px 10px;
  border-left: 4px solid #fcba03;
}

input,
select {
  padding: 5px 10px;
  width: 300px;
}

.optional-container {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  flex-wrap: wrap;
  width: 200px;
  margin-bottom: 20px;
  font-weight: bold;
}

.optional-container input {
  width: 30px;
}

#optional-title {
  width: 100%;
}

.submit-btn input {
  background: #222;
  color: #fcba03;
  font-weight: bold;
  border: 2px solid #222;
  padding: 10px;
  font-size: 16px;
  margin: 0 auto;
  cursor: pointer;
  transition: 0.4s;
  width: 300px;
}
.submit-btn input:hover {
  background: transparent;
  color: #222;
}
</style>