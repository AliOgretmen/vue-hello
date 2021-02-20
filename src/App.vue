<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div> {{ greet }} {{ name }} </div>
  <div v-text="date.getFullYear()"></div>
  <div v-html="country"></div>
  <h2 v-bind:id="headingid">Heading (2)</h2>
  <button v-bind:disabled="isDisabled">Bind</button>
  <h2 class="underline">Underlined Text</h2>
  <h3 class="underline" v-bind:class="status">Status</h3>
  <h2 v-bind:class="isPromoted && 'promoted'"> Promoted Code</h2>
  <h2 v-bind:class="isNew ? 'new' : 'old'"> New Text</h2>
  <h2 v-bind:class="['new', 'underline', 'promoted']"> Some Text</h2>
  <h2 v-bind:class="[isPromoted && 'promoted',isNew ? 'new' : 'old']"> Array Text</h2>
  <h2 v-bind:class="{
    promoted: isPromoted,
    old: !isNew,
    'new' : isNew
  }"> Object Text</h2>
  <h2 v-bind:style="{
    color: highlightCollor,
    'font-size': headerSize + 'px',
    padding: '20px'
  }"> Inline Style Text</h2>
    <h2 v-bind:style="headerObjectStyle"> Object Style Text</h2>
    <h2 :style="[baseObjectStyle, successObjectStyle]"> Array Style Text</h2>
</template>

<script>
export default {
  name: 'App',
  data(){  
    return{
      greet: "Hello",
      name: "Vue",
      date: new Date,
      country: "<b>Switzerland</b>",
      headingid: "Heading-id",
      isDisabled: true,
      status: "danger",
      isPromoted:true,
      isNew: true,
      highlightCollor: "orange",
      headerSize: 50,
      headerObjectStyle: {
        color: 'orange',
        fontSize: '50px',
        padding: '20px'
      },
      baseObjectStyle: {
        fontSize: '50px',
        padding: '10px'
      },
      successObjectStyle: {
        color: 'green',
        backgroundColor: 'lightgreen',
        border: '2px solid blue'
      }

    };
  },  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.underline{
  text-decoration: underline;
}

.promoted{
  font-style: italic;
}

.new{
  color: green;
}

.old{
  color: red;
}
</style>
