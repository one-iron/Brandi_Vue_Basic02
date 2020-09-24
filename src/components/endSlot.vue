<template>
  <div class="endSlot">
      <header>
        <slot name="end-header" />
      </header>
      <section>
        <slot name="end-container" />
      </section>
      <footer>
        <slot name="end-footer" />
      </footer>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
.endSlot {
    font-size: small;
    text-align: center;
    color:gray
}
</style>