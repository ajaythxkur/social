<template>
    <router-view/>
</template>

<style>
#app {
  font-family: MontserratAlternates, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: var(--ln-black);
  color: var(--ln-white);
}
:root{
  --ln-black: #000;
  --ln-white: #FFF;
  --ln-gray: #a6a2a2;
}
@font-face{
  font-family: MontserratAlternates;
  src: url('@/assets/fonts/MontserratAlternates/MontserratAlternates-Regular.ttf');
  font-weight: 400;
}
</style>
