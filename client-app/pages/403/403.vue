<template>
  <TwoColumn class="max-w-screen-lg">
    <template #left>
      <h1 class="text-primary text-7xl md:text-8xl font-black mb-5">403</h1>
      <h2 class="text-black-800 text-2xl md:text-4xl font-bold mb-2">Access denied</h2>
      <p class="text-gray-700 text-base md:text-xl leading-relaxed mb-10">
        You don't have permission to access requested page.
      </p>
      <div>
        <VcButton to="/" size="md" class="w-40 uppercase">Home page</VcButton>
      </div>
    </template>
    <template #right>
      <VcImage src="/static/images/errors/403.webp" alt="Access denied" class="w-full max-w-md" />
    </template>
  </TwoColumn>
</template>

<script setup lang="ts">
import { TwoColumn } from "@/shared/layout";
import { VcImage, VcButton } from "@/components";
</script>
