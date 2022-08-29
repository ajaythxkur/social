<template>
    <router-view/>
</template>

<style>
#app {
  font-family: JosefinSans, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: var(--ln-black);
  color: var(--ln-white);
}
/* Change the white to any color */
input:-webkit-autofill,
input:-webkit-autofill:hover, 
input:-webkit-autofill:focus, 
input:-webkit-autofill:active{
    -webkit-box-shadow: 0 0 0 30px var(--ln-black) inset !important;
}
:root{
  --ln-black: #000;
  --ln-white: #FFF;
  --ln-gray: #a6a2a2;
}
.layer{
  --ln-black: #FFF;
  --ln-white: #000;
  --ln-gray: #a6a2a2;
}
@font-face{
  font-family: JosefinSans;
  src: url('@/assets/fonts/JosefinSans/JosefinSans-VariableFont_wght.ttf');
  font-weight: 400;
}
/*****************skeltor loader css */

.vue-skeletor {
  position: relative;
  overflow: hidden;
  background-color: rgba(0, 0, 0, 0.12);
}

.vue-skeletor:not(.vue-skeletor--shimmerless):after {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  transform: translateX(-100%);
  background-image: linear-gradient(
    90deg,
    rgba(255, 255, 255, 0),
    rgba(255, 255, 255, 0.3),
    rgba(37, 22, 22, 0)
  );
  animation: shimmer 1.5s infinite;
  content: "";
}

.vue-skeletor--rect,
.vue-skeletor--circle {
  display: block;
}

.vue-skeletor--circle {
  border-radius: 50%;
}

.vue-skeletor--pill,
.vue-skeletor--text {
  border-radius: 9999px;
}

.vue-skeletor--text {
  line-height: 1;
  display: inline-block;
  width: 100%;
  height: inherit;
  vertical-align: middle;
  top: -1px;
}

@keyframes shimmer {
  100% {
    transform: translateX(100%);
  }
}

/*****************skeltor loader css *******/

</style>
