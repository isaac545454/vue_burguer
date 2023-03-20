<template>
  <div>
    <Message :msg="msg" v-show="msg" />
    <div>
      <form id="burguer-form" @submit="createBurger">
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
          <select id="bread" v-model="breadUser" placeholder="Digite seu Nome">
            <option value="">Selecione Seu Pão</option>
            <option v-for="b in bread" :key="b.id" :value="b.tipo">
              {{ b.tipo }}
            </option>
          </select>
        </div>
        <div class="input-container">
          <label for="meat"> Escolha o Carne </label>
          <select id="meat" v-model="meatUser" placeholder="Digite seu Nome">
            <option value="">Selecione o Tipo de Carne</option>
            <option v-for="m in meat" :key="m.id" :value="m.tipo">
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
              v-model="optionalUser"
              :value="o.tipo"
            />
            <span>{{ o.tipo }}</span>
          </div>
        </div>
        <div class="submit-btn">
          <input type="submit" class="submit-btn" value="criar meu Burguer" />
        </div>
      </form>
    </div>
  </div>
</template>

<script >
import { Vue, Options } from "vue-class-component";
import Message from "./message.vue";

@Options({
  components: {
    Message,
  },
})
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

  async createBurger(e) {
    e.preventDefault();
    const data = {
      nome: this.name,
      carne: this.meatUser,
      pao: this.breadUser,
      opcionais: Array.from(this.optionalUser),
      status: "Solicitado",
    };
    const stringData = JSON.stringify(data);
    await fetch("http://localhost:3000/burgers", {
      method: "POST",
      headers: { "content-type": "application/json" },
      body: stringData,
    })
      .then((res) =>
        res.json().then((res) => {
          console.log(res);
          this.optionalUser = [];
          this.meatUser = "";
          this.breadUser = "";
          this.name = "";
          this.msg = `Pedido Numero ${res.id} Realizado com Sucesso`;

          setTimeout(() => (this.msg = ""), 3000);
        })
      )
      .catch((err) => console.log(err));
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
  margin-bottom: 10px;
}

input,
select {
  padding: 5px 10px;
  width: 400px;
}

.optional-container {
  display: flex;

  justify-content: space-around;
  flex-wrap: wrap;
  width: 400px;
  margin-bottom: 20px;
  font-weight: bold;
}

.optional-container input,
.optional-container span {
  width: 20px;
  margin-top: 20px;
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
  width: 400px;
}
.submit-btn input:hover {
  background: transparent;
  color: #222;
}
</style>