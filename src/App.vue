<template>
    <div id="app">
      <Header/>
        <!-- <div id="nav">
            <router-link to="/">Home</router-link> | 
            <router-link to="/about">About</router-link>
        </div> -->
        <router-view/>
    </div>
</template>
<script>
import Header from './components/layouts/Header';
export default {
  components: {
    Header
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }

  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #FFF;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #777;
  }

</style>
