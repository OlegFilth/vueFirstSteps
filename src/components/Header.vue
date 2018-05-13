<template>
    <header class="header">
      <picture class="header__logo">
          <source media="(min-width: 767px)" srcset="../assets/images/logo-wide.png">
          <source srcset="../assets/images/logo.png">
          <img class="header__logo" src="../assets/images/logo.png" alt="Logo Duck">
      </picture>
    </header>
</template>

<script>
export default {
  
}
</script>


<style lang="scss">
  @import "../../node_modules/bootstrap/scss/functions";
  @import "../../node_modules/bootstrap/scss/variables";
  @import "../../node_modules/bootstrap/scss/mixins";
  @import "../assets/scss/abstracts/variables";
  @import "../assets/scss/layout/header";
</style>

