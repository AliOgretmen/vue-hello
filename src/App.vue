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

   <!-- Event Handling -->
  <h2>{{count}}</h2>
  <div>
    <button v-on:click="count +=1">Increment Count</button>
    <button v-on:click="count -=1">Decrement Count</button>
    <br>
    <button @click="increment(3, $event)">Increment Count</button>
    <button @click="decrement(2)">Decrement Count</button>
  </div>

 <h2>{{name}}</h2>
 <button @click="changeName($event), increment(17, $event)">Change Name</button>

  <!-- Form Handling -->
  <form @submit="submitForm">
    <div>
      <label for="name">Name</label>
      <input type="text" id="name" v-model.trim="formValues.name">
    </div>
      <div>
      <label for="profile">Profile Summary</label>
      <textarea id="profile" v-model="formValues.summary" />
    </div>
     <div>
      <label for="country">Country</label>
      <select id="country" v-model="formValues.country">
        <option value="">Select a country</option>
        <option value="FR">FR</option>
        <option value="DE">DE</option>
        <option value="CH">CH</option>
      </select>
    </div>
    <div>
      <label for="city">Location</label>
      <select id="city" v-model="formValues.city" multiple>
        <option value="Bern">Bern</option>
        <option value="Zurich">Zurich</option>
        <option value="Basel">Basel</option>
      </select>
    </div>
    <div>
      <input id="remoteWork" type="checkbox" v-model="formValues.remoteWork" true-value="yes" false-value="no"/>
      <label for="remoteWork">Open to remote work?</label>
    </div>
    <div>
      <label>Skill set</label>
      <input type="checkbox" id="html" value="html" v-model="formValues.skillSet" />
      <label for="html">HTML</label>
      <input type="checkbox" id="css" value="css" v-model="formValues.skillSet" />
      <label for="css">CSS</label>
      <input type="checkbox" id="javascript" value="javascript" v-model="formValues.skillSet"/>
      <label for="javascript">JavaScript</label>
    </div>
    <div>
      <label>Years of Experience</label>
      <input type="radio" id="0-2" value="0-2" v-model="formValues.yearsOfExperience" />
      <label for="0-2">0-2</label>
      <input type="radio" id="3-5" value="3-5" v-model="formValues.yearsOfExperience" />
      <label for="3-5">3-5</label>
      <input type="radio" id="6-10" value="6-10" v-model="formValues.yearsOfExperience" />
      <label for="6-10">5-10</label>
      <input type="radio" id="10+" value="10+" v-model="formValues.yearsOfExperience" />
      <label for="10+">10+</label>
    </div>
    <div>
      <label for="age">Age</label>
      <input type="number" id="age" v-model.number ="formValues.age" />
    </div>
    <div>
      <button>Submit</button>
    </div>
  </form>
  <div>
     {{ JSON.stringify(formValues) }}
  </div>

  <!-- Computed Properties -->
  <h2>Fullname - {{ firstName }} {{ lastName }}</h2>
  <h2>Fullname - {{ fullName }}</h2>
  <h2>
    Total - {{ items.reduce((total, curr) => (total = total + curr.price), 0) }}
  </h2>
  <h2>Computed Total - {{ total }}</h2>
  <h2>Method Total - {{ getTotal() }}</h2>
  <button @click="items.push({ id: 4, title: 'Keyboard', price: 50 })">
    Add item
  </button>


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
      count:0,
      name: 'Michael',
      firstName: 'Kai',
      lastName: 'Muller', 
      formValues:{
        name: '',
        summary: '',
        country: '',
        city: [],
        remoteWork: 'no',
        skillSet: [],
        yearsOfExperience: '',
        age: null,
      },
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
      },
      items: [
        {
          id: 1,
          title: 'TV',
          price: 100,
        },
        {
          id: 2,
          title: 'Phone',
          price: 200,
        },
        {
          id: 3,
          title: 'Laptop',
          price: 300,
        },
      ],
    }
  },
  methods:{
    add(a, b, c){
      return a + b + c
    },
    multiply(num) {
      return num * this.baseMultiplier
    },
    increment(num, event) {
      this.count += num
      console.log(event)
    },
    decrement(num) {
      this.count -= num
    },
    changeName(){
      this.name = 'Booby'
    },
    submitForm(event){
      event.preventDefault();
      console.log('Form', this.formValues)

    },
    getTotal() {
      console.log('getTotal method')
      return this.items.reduce((total, curr) => (total = total + curr.price), 0)
    },
  },
  computed:{
    fullName: {
      get() {
        return `${this.firstName} ${this.lastName}`
      },
      set(value) {
        const names = value.split(' ')
        this.firstName = names[0]
        this.lastName = names[1]
      },
    },
    total() { 
      console.log('total computed property')
      return this.items.reduce((total, curr) => (total = total + curr.price), 0)
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
label {
  font-weight: bold;
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}
input + label {
  font-weight: bold;
  display: inline-flex;
  margin-right: 20px;
}
input[type='text'],
textarea,
select {

  width: 400px;
  padding: 6px 12px;
  font-size: 14px;
  line-height: 1.42857143;
  color: #555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 4px;
}
</style>
