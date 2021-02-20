<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <!-- Binding Text -->
  <div> {{ greet }} {{ nameTest }} </div>
  <div v-text="date.getFullYear()"></div>

  <!-- Binding HTML -->
  <div v-html="country"></div>

  <!-- Bidning Attributes -->
  <h2 v-bind:id="headingid">Heading (2)</h2>
  <button v-bind:disabled="isDisabled">Bind</button>

  <!-- Bidning Classes -->
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

  <!-- Binding Inline Styles -->
  <h2 v-bind:style="{
    color: highlightCollor,
    'font-size': headerSize + 'px',
    padding: '20px'
  }"> Inline Style Text</h2>
    <h2 v-bind:style="headerObjectStyle"> Object Style Text</h2>
    <h2 :style="[baseObjectStyle, successObjectStyle]"> Array Style Text</h2>

<!-- Conditional Rendering -->
  <h1 v-if="num === 0">The number is zero</h1>
  <h2 v-else-if="num < 0">The number is negative</h2>
  <h2 v-else-if="num > 0">The number is positive</h2>
  <h2 v-else>Not a number</h2>
 <template v-if="showElement">
    <h2>Elemnent</h2>
 </template>
 <h2 v-show="showElement">Using v-show</h2>
  
 <!-- List Rendering -->

 <h4 v-for= "(name, index) in names" :key="name">{{index}} {{ name }}</h4>
 <h4 v-for="name in fullNames" :key="name.first"> {{name.first}} {{name.last}}</h4>
 <div v-for="actor in actors" :key="actor.name">
  <h3>{{actor.name}}</h3>
  <h4 v-for="movie in actor.movies" :key="movie"> {{movie}} </h4>
 </div>
 <h4 v-for="(value, key, index) in myObj" :key="value">{{index}} {{key}} {{value}}</h4>

 <div v-for="name in names" :key="name">
    <h2>{{ name }}</h2>
    <hr />
 </div>

 <div v-for="name in names" :key="name">
    <h2 v-if="(name == 'Hans')">{{ name }}</h2>
 </div>

  <!-- Methods -->
  <h2>Add Methods - {{ add(2, 3, 4) }}</h2>
  <h2>Multiply method - {{ multiply(10) }}</h2>
  <h2>Multiply method - {{ multiply(baseValue) }}</h2>


</template>

<script>
export default {
  name: 'App',
  data(){  
    return{
      greet: "Hello",
      nameTest: "Vue",
      date: new Date,
      country: "<b>Switzerland</b>",
      headingid: "Heading-id",
      isDisabled: true,
      status: "danger",
      isPromoted:true,
      isNew: true,
      highlightCollor: "orange",
      headerSize: 50,
      baseMultiplier: 4,
      baseValue: 2,
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
      },
      num: 123,
      showElement:true,
      names: ['Hans', 'Max', 'Tony'],
      fullNames: [
        {first: 'Hans', last: 'Mann'},
        {first: 'Max', last: 'Muster'},
        {first: 'Tony', last: 'Weber'}
      ],
      actors: [
        {
          name: 'Christian Bale',
          movies: ['Batman', 'American Psycho'],
        },
        {
          name: 'Di Caprio',
          movies: ['Titanic', 'Inception'],
        },
      ],
      myObj: {
        name: 'Tex',
        lastName: 'Mex',
        number: '43',
      }
    }
  },
  methods:{
    add(a, b, c){
      return a + b + c
    },
    multiply(num) {
      return num * this.baseMultiplier
    }, 
  }  
};
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
