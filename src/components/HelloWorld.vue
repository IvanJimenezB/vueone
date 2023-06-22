<script setup>
import { ref,computed, watch, watchEffect } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)

const classa = computed(()=> {
  return (count.value % 2) === 0 ? "red": "green"
});

const nombre = "Ivan"
const ape = "Burgos"

const fullname = computed(()=> `${nombre} ${ape}`)


const text = ref("Hola mundito de colores")

const op = true

const items = [
  {
    id: 1,
    name: "ivancito",
    description: "primera description de comentario"
  },
  {
    id: 23,
    name: "ivancitowwq",
    description: "seguda description de comentario"
  },
  {
    id: 3,
    name: "brocoli",
    description: "tercera description de comentario"
  }
]

const ultId = computed(()=> Math.max(...items.map(i => i.id)))

</script>

<template>
  <h1>{{ msg }}</h1>  <h1 v-text="text" ></h1>
  <h1 :class="classa">Hola mundo {{ classa }}</h1>
  <div class="card">
    <button type="button" @click="count++" :disabled="count == 15">count is {{ count }}</button>
    <button type="button" @click="count--" :disabled="count == -15">count is {{ count }}</button>
    <h1 v-text="fullname" :class="{red: op}" v-if="true"></h1>
    <input type="text" v-model="text" >
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
  <div>
    <div v-for="item in items" :key="item.id">
      <p v-text="item.name"></p>
      <span v-text="item.description"></span>
    </div>
  </div>
  <h1 v-text="ultId"></h1>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}

.red {
  color: red;
}

.green {
  color: purple;
}
</style>
