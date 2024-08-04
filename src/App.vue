<script setup>
import { ref } from "vue";
const items = ref([
  { item: "珍珠奶茶", desc: "香濃奶茶搭配QQ珍珠", price: 50, count: 20 },
  { item: "冬瓜檸檬", desc: "清新冬瓜配上新鮮檸檬", price: 45, count: 18 },
  { item: "珍珠奶茶", desc: "香濃奶茶搭配QQ珍珠", price: 50, count: 20 },
  { item: "冬瓜檸檬", desc: "清新冬瓜配上新鮮檸檬", price: 45, count: 18 },
]);

const minusCount = (index) => {
  items.value[index].count--;
};

const addCount = (index) => {
  items.value[index].count++;
};
</script>

<template>
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
      <tr v-for="(item, index) in items" :key="index">
        <td>{{ item.item }}</td>
        <td>
          <small>{{ item.desc }}</small>
        </td>
        <td>{{ item.price }}</td>
        <td>
          <button @click="minusCount(index)">-</button>
          {{ item.count }}
          <button @click="addCount(index)">+</button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped></style>
