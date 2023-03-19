<template>
  <div id="burguer-table">
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
      <div class="burguer-table-row">
        <div class="order-number">1</div>
        <div>Isaac</div>
        <div>pão</div>
        <div>Maminha</div>
        <div>
          <ul>
            <li>Salame</li>
            <li>Tomate</li>
          </ul>
        </div>
        <div>
          <select name="status" class="status">
            <option value="">aaaaaaaaaaaa</option>
          </select>
          <button class="delete-btn">Cancelar</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" >
import { Options, Vue } from "vue-class-component";
export default class Dashboard extends Vue {}
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

.order-number {
}

.status {
}

.delete-btn {
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