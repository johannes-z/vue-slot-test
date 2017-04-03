<template>
<th>
  {{ column }}
  <br>
  <select name="" id="" multiple>
    <option :value="value" v-for="value in data">
      {{ value }}
    </option>
  </select>
</th>
</template>

<script>
/**
 * This components template can be way more complex than depicted here.
 **/
export default {
  props: ['column', 'data']
}
</script>
