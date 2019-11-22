<template lang="pug">
  div(id="app")
    .wrapper
      header.header
        .container Ваха круто
      main.maincontent
        .container
          library
      footer.footer 
       .container очень круто
    
  
  
</template>

<script>
import library from './components/library.vue'

export default {
  name: 'app',
  components: {
    library
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Spectral+SC&display=swap');

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

/* http://meyerweb.com/eric/tools/css/reset/ 
   v2.0 | 20110126
   License: none (public domain)
*/

html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed, 
figure, figcaption, footer, header, hgroup, 
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
	margin: 0;
	padding: 0;
	border: 0;
	font-size: 100%;
	font: inherit;
	vertical-align: baseline;
  box-sizing: border-box;
  line-height: initial
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure, 
footer, header, hgroup, menu, nav, section {
	display: block;
}
body {
	line-height: 1;
}
ol, ul {
	list-style: none;
}
blockquote, q {
	quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: '';
	content: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}

html {height: 100%;
font-size: 1px}

body 
{height: 100%;
font-size: 16rem
}

img {max-width: 100%; 
max-height: 100%;
box-sizing: border-box;
display: block}

.wrapper {
  width: 100%;
  margin: 0 auto;
  height: 100vh;
  display: flex;
  flex-direction: column;
  
}

.container {
  width: 90%;
  margin: 0 auto
}

.header {
  flex: 0 0 auto;
 font-family: 'Spectral SC', serif;
 font-weight: bold;
 font-size: 52rem;
 text-align: center;
 color: #fff;
 background-color: #000;
}

.maincontent {
  flex: 1 0 auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
 
}

.footer {
    flex: 0 0 auto;
 font-family: 'Spectral SC', serif;
 font-weight: bold;
 font-size: 24rem;
 text-align: center;
 color: #fff;
 background-color: #000;
}


</style>
