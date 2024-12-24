<template>
  <q-page padding style="width: 1000px">
    <div style="font-size: 40px; font-weight: bold">Point of Sale</div>
    <div class="row full-width">
      <div class="col-6">
        <q-scroll-area style="height: 100%; max-width: 800px">
          <div class="row">
            <div v-for="p in products" :key="p.id" class="col-4">
              <ProductCard :product="p" @select="select"></ProductCard>
            </div></div
        ></q-scroll-area>
      </div>
      <div class="col-6">
        <q-scroll-area style="height: 80vh; max-width: 600px; width: 80vh">
          <table class="q-table">
            <thead>
              <th style="font-size: 24px">ชิ้นที่</th>
              <th style="font-size: 24px">ชื่อสินค้า</th>
              <th style="font-size: 24px">ราคา</th>
              <th style="font-size: 24px">จำนวน</th>
              <th style="font-size: 24px">จัดการสินค้า</th>
            </thead>
            <tbody>
              <tr v-for="(item, index) in productItems" :key="item.id">
                <td class="text-center" style="font-size: 15px">{{ item.id }}</td>
                <td class="text-center" style="font-size: 15px">{{ item.product.name }}</td>
                <td class="text-center" style="font-size: 15px">{{ item.product.price }} บาท</td>
                <td class="text-center" style="font-size: 15px">{{ item.amount }} ชิ้น</td>
                <td class="text-center" style="font-size: 15px">
                  <q-btn flat icon="delete" @click="removeItem(index)">ลบ</q-btn>
                </td>
              </tr>
            </tbody>
          </table>
        </q-scroll-area>
        <div class="text-h3">รวม {{ sumPrice }} บาท</div>
      </div>
    </div>
  </q-page>
</template>

<script setup lang="ts">
import ProductCard from 'src/components/ProductCard.vue'
import { type Product } from 'src/models'
import { computed, ref } from 'vue'
interface ProductItem {
  id: number
  product: Product
  amount: number
}
let lastProductItemId = 1
const products = ref<Product[]>([
  {
    id: 1,
    name: 'กาแฟ 1',
    price: 30,
    image: 'product1.png',
    size: 'ML',
  },
  {
    id: 2,
    name: 'กาแฟ 2',
    price: 20,
    image: 'product2.png',
    size: 'ML',
  },
  {
    id: 3,
    name: 'ขนมเค้ก 1',
    price: 45,
    image: 'product3.png',
    size: 'ML',
  },
  {
    id: 4,
    name: 'ขนมเค้ก 2',
    price: 20,
    image: 'product4.png',
    size: 'ML',
  },
  {
    id: 5,
    name: 'โกโก้',
    price: 35,
    image: 'product5.png',
    size: 'ML',
  },
  {
    id: 6,
    name: 'กาแฟ 3',
    price: 40,
    image: 'product6.png',
    size: 'ML',
  },
  {
    id: 7,
    name: 'กาแฟ 4',
    price: 30,
    image: 'product7.png',
    size: 'ML',
  },
  {
    id: 8,
    name: 'ชาเขียว ',
    price: 35,
    image: 'product8.png',
    size: 'ML',
  },
])

const productItems = ref<ProductItem[]>([])

function select(product: Product) {
  console.log(product)
  productItems.value.push({ id: lastProductItemId++, product: product, amount: 1 })
}

function removeItem(index: number) {
  productItems.value.splice(index, 1)
}

const sumPrice = computed(() => {
  let sum = 0
  for (let i = 0; i < productItems.value.length; i++) {
    sum = sum + productItems.value[i]!.product.price
  }
  return sum
})
</script>

<style>
body {
  background-color: cornsilk;
  color: brown;
}
</style>
