<template>
  <div id="app">
    <p v-if="hours < 12">Good morning!</p>
    <p v-if="hours >= 12 && hours < 18">Good afternoon!</p>
    <p v-if="hours >= 18">Good evening!</p>
    <p>Hello, {{greetee}}!</p>
    <p>The second dog is {{dogs[1]}}</p>
    <ul>
      <li v-for="dog in dogs">
        Dog name is {{dog}}
      </li>
    </ul>
    <button :type="buttonType" :disabled="buttonDisabled">Test Button</button>
    <p>have elapsed {{seconds}} seconds since you opened the page </p>
    <p>Current status {{getId(id)}}</p>
  </div>
</template>

<script>
  export default {
    name: 'HelloWorld',
    data() {
      return {
        msg: 'Welcome to Your Vue.js App',
        hours: new Date().getHours(),
        greetee: 'world',
        dogs: ['Rex', 'Rover', 'Henrietta', 'Alan'],
        buttonType: 'submit',
        buttonDisabled: true,
        seconds: 0,
        id: 2
      }
    },
    created() {
      setInterval(() => {
        this.seconds++;
        this.buttonDisabled = !this.buttonDisabled
      }, 1000)
    },
    methods: {
      getId(id) {
        const status = ({
          0: 'Asleep',
          1: 'Eating',
          2: 'Learning Vue'
        })[id];
        return status || 'Unknown: ' + id;
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1, h2 {
    font-weight: normal;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 0 10px;
  }

  a {
    color: #42b983;
  }
</style>
