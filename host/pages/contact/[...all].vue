<template>
  <div class="container mx-auto p-4">
    <h1 class="text-2xl font-bold mb-4">FinScore (Remote)</h1>
    <div class="grid grid-cols-1 gap-4">
      <client-only>
        <Suspense>
          <template #default>
            <RemoteContactRouter label="propsFromHost" @increment="handleLog" />
          </template>
          <template #fallback>
            <div>Loading Remote Component...</div>
          </template>
        </Suspense>
      </client-only>
    </div>
  </div>
</template>

<script setup lang="ts">
import { defineAsyncComponent } from "vue"

const handleLog = (value: number) => {
  console.log("HOST: log increment", value)
}
const RemoteContactRouter = defineAsyncComponent(
  // @ts-expect-error mfe
  () => import("remote/RemoteContactRouter")
)
</script>

<style scoped></style>
