<template>
  <div id="app">
    <div class="d-flex justify-content-center align-items-center">
      <a href="https://vuejs.org" target="blank" alt="Vue Logo"><img class="vue-logo" src="./assets/logo.png" /></a>
      <a href="https://github.com/patrickkunka/mixitup" target="blank" alt="Kunk MixItUp Logo">
        <div class="kunk-logo p-2">
          <svg class="logo_kunkalabs-glyph" viewBox="0 0 53.217 35.928">
            <polygon class="logo_kunkalabs-glyph__light" points="26.665,0 26.665,35.928 53.217,35.928"></polygon>
            <polygon class="logo_kunkalabs-glyph__dark" points="0,0 0,35.928 26.551,35.928"></polygon>
            <polygon class="logo_kunkalabs-glyph__light" points="0,35.928 0,0 26.551,0"></polygon>
            <polygon class="logo_kunkalabs-glyph__shadow" points="13.282,17.964 0,35.928 0,35.928 16.874,22.783"></polygon>
          </svg>
        </div>
      </a>
    </div>
    <h1>{{ msg }}</h1>

    <div class="controls">
      <button type="button" class="control" data-filter="all">All</button>
      <button type="button" class="control" data-filter=".green">Green</button>
      <button type="button" class="control" data-filter=".blue">Blue</button>
      <button type="button" class="control" data-filter=".pink">Pink</button>
      <button type="button" class="control" data-filter="none">None</button>

      <button type="button" class="control" data-sort="default:asc">Asc</button>
      <button type="button" class="control" data-sort="default:desc">Desc</button>
    </div>
    <div class="container">
      <div class="mix green"></div>
      <div class="mix green"></div>
      <div class="mix blue"></div>
      <div class="mix pink"></div>
      <div class="mix green"></div>
      <div class="mix blue"></div>
      <div class="mix pink"></div>
      <div class="mix blue"></div>

      <div class="gap"></div>
      <div class="gap"></div>
      <div class="gap"></div>
    </div>
  </div>
</template>

<script>
import mixitup from 'mixitup';

export default {
  name: 'app',
  data () {
    return {
      msg: 'Vue.js & MixItUp example'
    }
  },
  mounted() {
    var containerEl = document.querySelector('.container');
    var mixer = mixitup(containerEl);
  }
}
</script>

<style>
.kunk-logo {
  width: 12.5rem;
}
.logo_kunkalabs-glyph__light {
    fill: #5ecdde;
}
.logo_kunkalabs-glyph__dark {
    fill: #27aabe;
}
.logo_kunkalabs-glyph__light {
    fill: #5ecdde;
}
.logo_kunkalabs-glyph__shadow {
    fill: #249bad;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #222222;
  margin-top: 20px;
}
html,
body {
  height: 100%;
  background: #f2f2f2;
}
.vue-logo {
  width: 150px;
  max-width: 100%;
  height: auto;
}
*,
*:before,
*:after {
    box-sizing: border-box;
}

/* Controls
---------------------------------------------------------------------- */

.controls {
    padding: 1rem;
    background: #333;
    font-size: 0.1px;
}

.control {
    position: relative;
    display: inline-block;
    width: 2.7rem;
    height: 2.7rem;
    background: #444;
    cursor: pointer;
    font-size: 0.1px;
    color: white;
    transition: background 150ms;
}

.control:hover {
    background: #3f3f3f;
}

.control[data-filter]:after {
    content: '';
    position: absolute;
    width: 10px;
    height: 10px;
    top: calc(50% - 6px);
    left: calc(50% - 6px);
    border: 2px solid currentColor;
    border-radius: 2px;
    background: currentColor;
    transition: background-color 150ms, border-color 150ms;
}

.control[data-sort]:after {
    content: '';
    position: absolute;
    width: 10px;
    height: 10px;
    border-top: 2px solid;
    border-left: 2px solid;
    top: calc(50% - 6px);
    left: calc(50% - 6px);
    transform:  translateY(1px) rotate(45deg);
}

.control[data-sort*=":desc"]:after {
    transform:  translateY(-4px) rotate(-135deg);
}

.mixitup-control-active {
    background: #393939;
}

.mixitup-control-active[data-filter]:after {
    background: transparent;
}

.control:first-of-type {
    border-radius: 3px 0 0 3px;
}

.control:last-of-type {
    border-radius: 0 3px 3px 0;
}

.control[data-filter] + .control[data-sort] {
    margin-left: .75rem;
}

.control[data-filter=".green"] {
    color: #91e6c7;
}

.control[data-filter=".blue"] {
    color: #5ecdde;
}

.control[data-filter=".pink"] {
    color: #d595aa;
}

.control[data-filter="none"] {
    color: #2f2f2f;
}

/* Container
---------------------------------------------------------------------- */

.container {
    padding: 1rem;
    text-align: justify;
    font-size: 0.1px;
}

.container:after {
    content: '';
    display: inline-block;
    width: 100%;
}

/* Target Elements
---------------------------------------------------------------------- */

.mix,
.gap {
    display: inline-block;
    vertical-align: top;
}

.mix {
    background: #fff;
    border-top: .5rem solid currentColor;
    border-radius: 2px;
    margin-bottom: 1rem;
    position: relative;
}

.mix:before {
    content: '';
    display: inline-block;
    padding-top: 56.25%;
}

.mix.green {
    color: #91e6c7;
}

.mix.pink {
    color: #d595aa;
}

.mix.blue {
    color: #5ecdde;
}

/* Grid Breakpoints
---------------------------------------------------------------------- */

/* 2 Columns */

.mix,
.gap {
    width: calc(100%/2 - (((2 - 1) * 1rem) / 2));
}

/* 3 Columns */

@media screen and (min-width: 541px) {
    .mix,
    .gap {
        width: calc(100%/3 - (((3 - 1) * 1rem) / 3));
    }
}

/* 4 Columns */

@media screen and (min-width: 961px) {
    .mix,
    .gap {
        width: calc(100%/4 - (((4 - 1) * 1rem) / 4));
    }
}

/* 5 Columns */

@media screen and (min-width: 1281px) {
    .mix,
    .gap {
        width: calc(100%/5 - (((5 - 1) * 1rem) / 5));
    }
}
</style>
