<script setup>
import { ref } from 'vue'

const data = [
  {
    id: 1,
    name: '珍珠奶茶',
    descrption: '香濃奶茶搭配QQ珍珠',
    price: 50,
    stock: 20,
    isEdit: false,
  },
  {
    id: 2,
    name: '冬瓜檸檬',
    descrption: '清新冬瓜配上新鮮檸檬',
    price: 45,
    stock: 18,
    isEdit: false,
  },
  {
    id: 3,
    name: '翡翠檸檬',
    descrption: '綠茶與檸檬的完美結合',
    price: 55,
    stock: 34,
    isEdit: false,
  },
  {
    id: 4,
    name: '四季春茶',
    descrption: '香醇四季春茶，回甘無比',
    price: 45,
    stock: 10,
    isEdit: false,
  },
  {
    id: 5,
    name: '阿薩姆奶茶',
    descrption: '阿薩姆紅茶搭配香醇鮮奶',
    price: 50,
    stock: 25,
    isEdit: false,
  },
  {
    id: 6,
    name: '檸檬冰茶',
    descrption: '檸檬與冰茶的清新組合',
    price: 45,
    stock: 20,
    isEdit: false,
  },
  {
    id: 7,
    name: '芒果綠茶',
    descrption: '芒果與綠茶的獨特風味',
    price: 55,
    stock: 18,
    isEdit: false,
  },
  {
    id: 8,
    name: '抹茶拿鐵',
    descrption: '抹茶與鮮奶的絕配',
    price: 60,
    stock: 20,
    isEdit: false,
  },
]
const menu = ref(data)

const handleMenuStock = (id, stock) => {
  menu.value = menu.value.map((item) => {
    if (item.id === id) {
      item.stock = stock
    }
    return item
  })
}
</script>

<template>
  <div class="container">
    <h1>Vue Week1 餐點管理工具</h1>
    <hr />
    <table>
      <thead>
        <tr>
          <th scope="col">品項</th>
          <th scope="col">描述</th>
          <th scope="col">價格</th>
          <th scope="col">庫存</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in menu" v-bind:key="item.id">
          <td>{{ item.name }}</td>
          <td>
            <small>{{ item.descrption }}</small>
          </td>
          <td>{{ item.price }}</td>
          <td>
            <button
              type="button"
              class="btn"
              v-on:click="handleMenuStock(item.id, item.stock - 1)"
              v-bind:disabled="item.stock < 1"
            >
              -
            </button>
            {{ item.stock }}
            <button type="button" class="btn" v-on:click="handleMenuStock(item.id, item.stock + 1)">
              +
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped>
.container {
  max-width: 1296px;
  margin: 0 auto;
}
table {
  width: 100%;
  font-size: 20px;
}
td,
th {
  border-bottom: 1px solid #e5e5e5;
  padding: 8px 20px;
  text-align: center;
}

.btn {
  margin: 5px;
  border: none;
  background-color: lightgrey;
  padding: 4px 18px;
  border-radius: 50px;
  font-size: 18px;
}
</style>
