<template>
  <div class="box has-text-weight-bold">
    <slot>
      
    </slot>
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'BoxCard'

})
</script>
<style scoped>
.box{
  background-color: rgb(19, 32, 43);
}
</style>