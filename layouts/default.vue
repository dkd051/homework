<template>
  <div>
    <Nuxt />
  </div>
</template>

<style lang="scss">
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  background-size: cover;
  background-position: center top;
  background-repeat: no-repeat;
}


html {
  font-family: system-ui,"AppleSDGothicNeo",sans-serif;
  font-size: 62.5%;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

html,body,div,span,applet,object,iframe,h1,h2,h3,h4,h5,h6,p,blockquote,pre,a,abbr,acronym,address,big,cite,code,del,dfn,em,img,ins,kbd,q,s,samp,small,strike,strong,sub,sup,tt,var,b,u,i,center,dl,dt,dd,ol,ul,li,fieldset,form,label,legend,table,caption,tbody,tfoot,thead,tr,th,td,article,aside,canvas,details,embed,figure,figcaption,footer,header,hgroup,menu,nav,output,ruby,section,summary,time,mark,audio,video,button {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 62.5%;
  font: inherit;
  vertical-align: baseline;
  background-position: center;
}

article,aside,details,figcaption,figure,footer,header,hgroup,menu,nav,section {
  display: block
}

body {
  line-height: 1;
  overflow-x: hidden;
  font-size: 62.5%;
  height: 100vh;
  // overflow: hidden;
  &.open-modal {
    // overflow: hidden;
    // position: fixed
  }
}

ol,ul {
  list-style: none
}

button {
    outline: 0;
    background-color: unset;
    border: 0;
    background-position: center center;
    background-repeat: no-repeat;
}

img{
  max-width: 100%;
}

.ir{
  display: block;
  overflow: hidden;
  color: transparent;
  white-space: nowrap;
  background-size: cover;
  line-height: 0;
}

.blind{
    overflow: hidden;
    position: absolute;
    top: 0;
    left: 0;
    width: 1px;
    height: 1px;
    font-size: 0;
    line-height: 0;
}

body{
  background-color: #2e2925;
  // background-size: cover;
  // *{
  //   background-size: inherit;
  // }
}
</style>
