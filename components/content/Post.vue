<template>
  <section
    class="container mx-auto h-screen grid grid-rows-3 gap-4 justify-items-center items-center"
  >
    <div class="text-slate-300 max-w-[61.8%]">
      <slot name="prompt" />
    </div>
    <div class="row-start-2 max-w-fit">
      <slot id="code" />
    </div>
  </section>
</template>
