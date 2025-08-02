<script setup>
import {ref} from 'vue';

const menuItems = ref([
  {
    name: '珍珠奶茶',
    description: '香濃奶茶搭配QQ珍珠',
    price: 50,
    stock: 20,
    isEditing: false,
    tempName: ''
  },
  {
    name: '冬瓜檸檬',
    description: '清新冬瓜配上新鮮檸檬',
    price: 45,
    stock: 18,
    isEditing: false,
    tempName: ''
  },
  {
    name: '翡翠檸檬',
    description: '綠茶與檸檬的完美結合',
    price: 55,
    stock: 34,
    isEditing: false,
    tempName: ''
  },
  {
    name: '四季春茶',
    description: '香醇四季春茶，回甘無比',
    price: 45,
    stock: 10,
    isEditing: false,
    tempName: ''
  },
  {
    name: '阿薩姆奶茶',
    description: '阿薩姆紅茶搭配香醇鮮奶',
    price: 50,
    stock: 25,
    isEditing: false,
    tempName: ''
  },
  {
    name: '檸檬冰茶',
    description: '檸檬與冰茶的清新組合',
    price: 45,
    stock: 20,
    isEditing: false,
    tempName: ''
  },
  {
    name: '芒果綠茶',
    description: '芒果與綠茶的獨特風味',
    price: 55,
    stock: 18,
    isEditing: false,
    tempName: ''
  },
  {
    name: '抹茶拿鐵',
    description: '抹茶與鮮奶的絕配',
    price: 60,
    stock: 20,
    isEditing: false,
    tempName: ''
  }
]);

const addClick = (index) => {
  if (menuItems.value[index].stock >= 0) {
    menuItems.value[index].stock++;
  }
}

const decreaseClick = (index) => {
  if (menuItems.value[index].stock !== 0) {
    menuItems.value[index].stock--;
  }
}

const editClick = (index) =>{
  menuItems.value[index].isEditing = true;
  menuItems.value[index].tempName = menuItems.value[index].name;
}

const confirmClick = (index) => {
  menuItems.value[index].name = menuItems.value[index].tempName;
  menuItems.value[index].isEditing = false;
  
}

</script>

<template>
    <div class="center-wrapper">
        <table class="p-10 mx-auto">
          <thead>
            <tr>
              <th scope="col">品項</th>
              <th scope="col">描述</th>
              <th scope="col">價格</th>
              <th scope="col"></th>
              <th scope="col">庫存</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(item, index) in menuItems" :key="item.name">
              <td>
                <div v-if="item.isEditing">
                  <input type="text" v-model="item.tempName" />
                </div>
                <div v-else>
                  {{ item.name }}
                </div>
              </td>
              <td>{{ item.description }}</td>
              <td>{{ item.price }} 元</td>
              <td>
                <button class="btn btn-primary" @click="addClick(index)"> + </button>
              </td>
              <td>{{ item.stock }} 件</td>
              <td>
                <button class="btn btn-primary" @click="decreaseClick(index)"> - </button>
              </td>
              <td>
                <div v-if="item.isEditing">
                  <button class="btn btn-primary" @click="confirmClick(index)">確認</button>
                </div>
                <div v-else>
                  <button class="btn btn-primary" @click="editClick(index)">編輯</button>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
    </div>

</template>