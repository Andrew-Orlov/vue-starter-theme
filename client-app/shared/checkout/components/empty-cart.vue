<template>
  <TwoColumn class="max-w-screen-lg">
    <template #left>
      <div class="flex flex-col h-full py-12 justify-center items-center lg:items-start">
        <VcImage src="/static/images/errors/emptyCartMobile.webp" alt="emptyCartMobile" class="lg:hidden mb-8" />
        <h2 class="text-black-800 text-2xl md:text-4xl font-bold mb-8">Your cart is empty</h2>
        <VcButton :to="`/${SeoUrl.Catalog}`" size="lg" class="w-48 uppercase font-bold">Continue shopping</VcButton>
      </div>
    </template>
    <template #right>
      <VcImage src="/static/images/errors/emptyCart.webp" alt="emptyCart" class="w-full max-w-md" />
    </template>
  </TwoColumn>
</template>

<script setup lang="ts">
import { VcImage, VcButton } from "@/components";
import { TwoColumn } from "@/shared/layout";
import SeoUrl from "@core/seo-routes.enum";
</script>
