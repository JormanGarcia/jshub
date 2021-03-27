<template>
  <div>
    <Header />
    <Nuxt />
    <footer>This is a demo created by <strong>Jorman Garcia</strong> you can see the repo <a href="#" >here</a></footer>
  </div>
</template>
<style>

footer {
  text-align: center;
  padding: 50px 0;
  opacity: .8;
  width: 95vw;
  margin: auto;
  max-width: 1200px;
}

footer a {
  opacity: .5;
}

footer a:hover {
  color: var(--main-color);
  opacity: 1;
}


</style>


