<template>
  <div class="content">
    <p>Maximele din clase:</p>
    <h3>{{ maxValues }}</h3>
  </div>
</template>

<script>
export default {
  props: ["maxValues"],
};
</script>
