<template>
  <div
    class="h-12 px-12 flex items-center justify-end bg-[color:var(--color-header-top-bg)] font-bold text-sm text-[color:var(--color-header-top-text)]"
  >
    <!-- Authorized menu items -->
    <div v-if="isAuthenticated" class="flex items-center">
      <TopHeaderLink to="/account/dashboard">Dashboard</TopHeaderLink>
      <div class="mx-3 h-1 w-1 bg-[color:var(--color-primary)] rounded"></div>
      <TopHeaderLink to="/account/orders">Order History</TopHeaderLink>
      <div class="mx-3 h-1 w-1 bg-[color:var(--color-primary)] rounded"></div>
      <TopHeaderLink to="/500">Lists</TopHeaderLink>
      <div class="w-px h-5 bg-[color:var(--color-primary)] mx-4 hidden lg:block"></div>

      <!-- Account menu -->
      <div ref="loginMenu" class="relative cursor-pointer">
        <div class="flex items-center" @click="loginMenuVisible = !loginMenuVisible">
          <div>{{ me.contact?.fullName }}</div>
          <i class="fas fa-chevron-down ml-3 text-[color:var(--color-primary)] align-baseline"></i>
        </div>
        <div
          v-if="loginMenuVisible"
          class="absolute z-10 bg-white rounded-md shadow-lg flex flex-col px-3 py-4 space-y-3 mt-2 right-0 text-black"
        >
          <div class="flex items-center justify-between">
            <i class="fa fa-user-circle fa-2x fa-fw text-[color:var(--color-primary)]"></i>
            <span class="ml-2">{{ me.contact?.fullName }}</span>
            <button
              class="ml-4 text-gray-400 hover:bg-gray-200 border border-gray-200 rounded h-6 w-6 shadow"
              @click="signOut"
            >
              <i class="fas fa-sign-out-alt"></i>
            </button>
          </div>
        </div>
      </div>
    </div>

    <!-- Unauthorized menu items -->
    <div v-else class="flex items-center">
      <TopHeaderLink to="/sign-in">Sign In</TopHeaderLink>
      <div class="mx-3 h-1 w-1 bg-[color:var(--color-primary)] rounded"></div>
      <TopHeaderLink to="/sign-up">Register now</TopHeaderLink>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { onClickOutside } from "@vueuse/core";
import { useUser } from "@/shared/account";
import TopHeaderLink from "./top-header-link.vue";

const { isAuthenticated, me, signMeOut } = useUser();
const loginMenu = ref(null);
const loginMenuVisible = ref(false);

async function signOut() {
  await signMeOut();
  location.href = "/";
}

onClickOutside(loginMenu, () => {
  loginMenuVisible.value = false;
});
</script>
