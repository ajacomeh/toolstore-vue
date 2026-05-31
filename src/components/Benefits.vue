<script setup>

import {
  Truck,
  ShieldCheck,
  Wrench
} from "lucide-vue-next"

const benefits = [

  {
    icon: Truck,
    text: "Entrega rápida"
  },

  {
    icon: ShieldCheck,
    text: "Garantía de calidad"
  },

  {
    icon: Wrench,
    text: "Soporte técnico"
  }

]

</script>

<template>

  <section
    id="benefits"
    class="benefits"
  >

    <h2>
      ¿Por qué elegirnos?
    </h2>

    <div class="benefit-container">

      <div
        v-for="(item,index) in benefits"
        :key="index"
        class="benefit-card"
      >

        <div class="icon">

          <component
            :is="item.icon"
            :size="50"
          />

        </div>

        <h3>
          {{ item.text }}
        </h3>

      </div>

    </div>

  </section>

</template>