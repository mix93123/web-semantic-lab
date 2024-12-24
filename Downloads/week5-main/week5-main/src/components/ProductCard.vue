<template>
  <q-card class="my-card">
    <q-img :src="product.image" style="height: 140px; width: 140px; object-fit: cover">
      <div class="absolute-bottom text-center">
        <div class="text-h6">{{ product.name }}</div>
        <div class="text-subtitle2">{{ product.price }} บาท</div>
      </div>
    </q-img>
    <q-card-actions class="center-actions">
      <q-btn flat @click="select" class="button-with-border">Select</q-btn>
    </q-card-actions>
  </q-card>
</template>

<script setup lang="ts">
import { type Product } from 'src/models'

const props = defineProps<{
  product: Product
}>()

const emit = defineEmits<{
  select: [product: Product]
}>()

function select() {
  emit('select', props.product)
}
</script>

<style lang="scss" scoped>
.my-card {
  width: 100%;
  max-width: 140px;
}

.center-actions {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 50px;
}

.button-with-border {
  border: 2px solid brown;
  padding: 5px 20px;
  border-radius: 5px;
  color: solid brown;
}

.button-with-border:hover {
  background-color: cornsilk;
  color: red;
}
</style>
