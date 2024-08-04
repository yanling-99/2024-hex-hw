<script setup>
import { ref } from "vue";
const items = ref([
  { item: "珍珠奶茶", desc: "香濃奶茶搭配QQ珍珠", price: 50, count: 20 },
  { item: "冬瓜檸檬", desc: "清新冬瓜配上新鮮檸檬", price: 45, count: 18 },
  { item: "翡翠檸檬", desc: "綠茶與檸檬的完美結合", price: 55, count: 34 },
  { item: "四季春茶", desc: "香醇四季春茶，回甘無比", price: 45, count: 10 },
  { item: "阿薩姆奶茶", desc: "阿薩姆紅茶搭配香醇鮮奶", price: 50, count: 25 },
  { item: "檸檬冰茶", desc: "檸檬與冰茶的清新組合", price: 45, count: 20 },
  { item: "芒果綠茶", desc: "芒果與綠茶的獨特風味", price: 55, count: 18 },
  { item: "抹茶拿鐵", desc: "抹茶與鮮奶的絕配", price: 60, count: 20 },
]);
const isEditItemName = ref(false);
const editIndex = ref(-1);
const newItemName = ref("");

const updateCount = (index, amount) => {
  items.value[index].count += amount;
};

const editItemName = (index) => {
  isEditItemName.value = !isEditItemName.value;
  editIndex.value = index;
  newItemName.value = items.value[index].item;
};

const cancelBtn = (index) => {
  isEditItemName.value = !isEditItemName.value;
};

const confirmBtn = (index) => {
  items.value[index].item = newItemName.value;
  isEditItemName.value = !isEditItemName.value;
  editIndex.value = 0;
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
        <th scope="col">操作</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(item, index) in items" :key="index">
        <input
          v-if="isEditItemName && editId === index"
          type="text"
          v-model="newItemName"
        />
        <td v-else>{{ item.item }}</td>

        <td>
          <small>{{ item.desc }}</small>
        </td>
        <td>{{ item.price }}</td>
        <td>
          <button @click="updateCount(index, -1)" :disabled="item.count === 0">
            -
          </button>
          {{ item.count }}
          <button @click="updateCount(index, 1)">+</button>
        </td>
        <td v-if="isEditItemName && editId === index">
          <button @click="confirmBtn(index)">確定</button>
        </td>
        <td v-if="isEditItemName && editId === index">
          <button @click="cancelBtn(index)">取消</button>
        </td>
        <td v-else><button @click="editItemName(index)">編輯品名</button></td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped></style>
