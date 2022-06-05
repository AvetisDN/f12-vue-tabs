<script setup>
import { ref, shallowRef } from "vue";
import Tab1 from "./tabs/Tab1.vue";
import Tab2 from "./tabs/Tab2.vue";
import Tab3 from "./tabs/Tab3.vue";

const active = shallowRef(Tab1);
</script>

<template>
  <div class="w-full min-h-screen bg-base-200 flex items-center justify-center">
    <div class="bg-base-100 p-4 rounded shadow w-[520px]">
      <div class="tabs justify-center">
        <a
          class="tab tab-bordered"
          :class="{ 'tab-active': active === Tab1 }"
          @click="active = Tab1"
        >
          Tab 1
        </a>
        <a
          class="tab tab-bordered"
          :class="{ 'tab-active': active === Tab2 }"
          @click="active = Tab2"
        >
          Tab 2
        </a>
        <a
          class="tab tab-bordered"
          :class="{ 'tab-active': active === Tab3 }"
          @click="active = Tab3"
        >
          Tab 3
        </a>
      </div>
      <div class="min-h-[120px] py-4">
        <Transition name="fade" mode="out-in">
          <component :is="active"></component>
        </Transition>
      </div>
    </div>
  </div>
</template>
<style>
.fade-enter-active,
.fade-leave-active {
  transition: all 0.5s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translatey(50px);
}
</style>
