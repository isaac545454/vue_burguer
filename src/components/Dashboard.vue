<template>
  <div id="burguer-table">
    <Message :msg="msg" v-show="msg" />
    <div>
      <div id="burguer-table-heading">
        <div class="order-id">#:</div>
        <div>Cliente:</div>
        <div>Pão:</div>
        <div>Carne:</div>
        <div>Opcionais:</div>
        <div>Ações:</div>
      </div>
    </div>
    <div id="burguer-table-rows">
      <div class="burguer-table-row" v-for="b in burguers" :key="b.id">
        <div class="order-number">{{ b.id }}</div>
        <div>{{ b.nome }}</div>
        <div>{{ b.pao }}</div>
        <div>{{ b.carne }}</div>
        <div>
          <ul>
            <li v-for="(o, index) in b.opcionais" :key="index">
              {{ o }}
            </li>
          </ul>
        </div>
        <div>
          <select
            name="status"
            class="status"
            @change="updatedBurguer($event, b.id)"
          >
            <option
              v-for="s in status"
              :key="s.id"
              :value="s.tipo"
              :selected="b.status == s.tipo"
            >
              {{ s.tipo }}
            </option>
          </select>
          <button class="delete-btn" @click="deleteBurguer(b.id)">
            Cancelar
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script  >
import { Vue, Options } from "vue-class-component";
import Message from "./message.vue";

@Options({
  components: {
    Message,
  },
})
export default class Dashboard extends Vue {
  data() {
    return {
      burguers: null,
      burguers_id: null,
      status: [],
      msg: null,
    };
  }

  async getRequests() {
    const res = await fetch("http://localhost:3000/burgers");
    const data = await res.json();
    this.burguers = data;
    console.log(this.burguers);
  }

  async getRequestsStatus() {
    const res = await fetch("http://localhost:3000/status");
    const data = await res.json();
    this.status = data;
    console.log(this.status);
  }

  async deleteBurguer(id) {
    const res = await fetch(`http://localhost:3000/burgers/${id}`, {
      method: "DELETE",
      headers: { "content-type": "application/json" },
    });
    await res.json().then(() => {
      this.getRequests();

      this.msg = "Pedido cancelado com sucesso";
      setTimeout(() => (this.msg = ""), 3000);
    });
  }

  async updatedBurguer(event, id) {
    const option = event.target.value;
    await fetch(`http://localhost:3000/burgers/${id}`, {
      method: "PATCH",
      headers: { "content-type": "application/json" },
      body: JSON.stringify({ status: option }),
    }).then(() => {
      this.msg = "Pedido Atualizado com sucesso";
      setTimeout(() => (this.msg = ""), 3000);
    });
  }

  mounted() {
    this.getRequests();
    this.getRequestsStatus();
  }
}
</script>

<style scoped>
#burguer-table {
  max-width: 1200px;
  margin: 0 auto;
}
#burguer-table-heading,
.burguer-table-row,
#burguer-table-rows {
  display: flex;
  flex-wrap: wrap;
}

#burguer-table-heading {
  font-weight: bold;
  padding: 12px;
  border-bottom: 3px solid #333;
  display: flex;
  flex-wrap: wrap;
}

#burguer-table-heading div,
.burguer-table-row div {
  width: 19%;
}
#burguer-table-heading .order-id,
.burguer-table-row .order-number {
  width: 5%;
}

#burguer-table-rows {
  display: flex;
  flex-wrap: wrap;
}

.burguer-table-row {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  padding: 12px;
  border-bottom: 1px solid #ccc;
}

select {
  padding: 12px 6px;
  margin-right: 12px;
  border-radius: 10px;
}

.delete-btn {
  background-color: #222;
  color: #fcba03;
  font-weight: bold;
  border: 2px solid #222;
  padding: 10px;
  cursor: pointer;
  margin: 0 auto;
  transition: 0.5s;
}
.delete-btn:hover {
  background-color: transparent;
  color: #222;
}
</style>