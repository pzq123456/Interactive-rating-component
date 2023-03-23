<script setup>
import MyComp1 from './components/MyComp1.vue'
</script>

<template>
  <MyComp1 />
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Overpass:wght@400;700&display=swap');
:root{
    --orange: hsl(25, 97%, 53%);
    --white: hsl(0, 0%, 100%);
    --light-grey: hsl(217, 12%, 63%);
    --medium-grey: hsl(216, 12%, 54%);
    --medium-grey-2: hsla(216, 12%, 54%, 0.227);
    --dark-blue: hsl(213, 19%, 18%);
    --very-dark-blue: hsl(216, 12%, 8%);
    --very-dark-blue-2: hsl(225, 8%, 10%);
}

*{
    margin: 0;
    box-sizing: border-box;
    padding: 0;
    font-family: overpass, sans-serif;
}

p{
  font-size: 15px;
}

</style>
