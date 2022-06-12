<template>
  <div class="card">
    <h1>{{title}}</h1>
    <!--<div v-if="showModal">
      <Modal @close="toggleModal">
        <template v-slot:links>
          <a href="#">sign up</a>
        </template>
        <h1>new new</h1>
        <p>new paragraph as well</p>

      </Modal>
    </div>-->
    <input id="inputWord" @keyup.enter="getData" placeholder="write a word" type="text" v-model="myInput" ref="name">
    <button id="buttonWord" @click="getData">Search</button>
    <!--<button @click="toggleModal">show modal</button>-->
    <div v-if="showModal">  
      <Maincard :wordd=wordd :partOfSpeech=partOfSpeech :audiosrc=audiosrc :phoneticc=phoneticc :synonyms=synonyms>      
      </Maincard>
      <Meanings :meaning=meaning :wordd=wordd :meanings=meanings />
      <Examples :wordd=wordd :examples=examples />
    </div>
    
  </div>
</template>

<script>
  import Modal from './components/Modal.vue'
  import axios from 'axios'
  import Maincard from './components/Maincard.vue'
  import Meanings from './components/Meanings.vue'
  import Examples from './components/Examples.vue'
  export default {
    name: 'App',
    components: {
      Modal,
      Maincard,
      Meanings,
      Examples
    },
    data() {
      return {
        myInput: '',
        title: 'My first vue app',
        header: 'Sign up for the giveaway',
        texts: 'hello dearest',
        showModal: false,
        wordd: '',
        activ: false,
        phoneticc: '',
        partOfSpeech: '',
        audiosrc: '',
        audiosrc1: '',
        meaning: '',
        meanings: [],
        synonyms: '',
        examples: [],
      }
    },
    methods: {
      handleClick() {
        console.log(this.$refs.name);
        this.$refs.name.classList.add('active')
        this.$refs.name.focus()
      },
      toggleModal() {
        this.showModal = !this.showModal
      },
      playSound (sound) {
        if(sound) {
          var audio = new Audio(sound);
          audio.play();
        }
      },
      getData() {
        this.showModal = true;
        axios
          .get('https://api.dictionaryapi.dev/api/v2/entries/en/' + this.myInput)
          .then(response => (
            this.wordd = response["data"][0].word,
            this.partOfSpeech = response["data"][0]["meanings"][0].partOfSpeech,
            this.phoneticc = response["data"][0]["phonetics"][0].text,
            this.audiosrc = response["data"][0]["phonetics"][0].audio,
            this.audiosrc1 = response["data"][0]["phonetics"][1] ? response["data"][0]["phonetics"][1].audio : '',
            this.meanings = response["data"][0]["meanings"][0].definitions,
            this.synonyms = response["data"][0]["meanings"][0].synonyms[0],
            this.examples = this.meanings.filter((example) => {
              return example.example !== undefined
            })
          ))
      },
    }
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

  .modal .actions {
    text-align: center;
    margin: 30px 0 10px 0;
  }

  .modal .actions a {
    color: #333333;
    padding: 8px;
    border: 1px solid #eee;
    border-radius: 4px;
    text-decoration: none;
    margin: 10px;
  }

  #inputWord {
    top: 18%;
    left: 5%;
    position: absolute;
    border: 1px solid #eee;
    background: rgba(51, 51, 51, 0.613);
    border-radius: 8px;
    width: 45%;
    height: 40px;
    color: white;
  }

  #buttonWord {
    top: 18%;
    left: 52%;
    position: absolute;
    border: 1px solid #eee;
    background: rgba(51, 51, 51, 0.59);
    border-radius: 8px;
    width: 13%;
    height: 43px;
    color: white;
    cursor: pointer;
  }
  .maincard{
    margin-top: 12%;
    text-align: left;
    margin-left: 5%;
    padding: 1%;
    width: 70%;
    border-radius: 10px;
    background-color: #e1bebead;
    box-shadow: rgba(50, 50, 93, 0.2) 0px 50px 100px -20px, rgba(0, 0, 0, 0.2) 0px 30px 60px -30px;
  }
  .meaningcard{
    margin-top: 5%;
    text-align: left;
    margin-left: 5%;
    padding: 1%;
    width: 70%;
    border-radius: 10px;
    background-color: #e1bebead;
    box-shadow: rgba(50, 50, 93, 0.2) 0px 50px 100px -20px, rgba(0, 0, 0, 0.2) 0px 30px 60px -30px;
  }
  .examplecard{
    margin-top: 5%;
    text-align: left;
    margin-left: 5%;
    padding: 1%;
    width: 70%;
    border-radius: 10px;
    background-color: #e1bebead;
    box-shadow: rgba(50, 50, 93, 0.2) 0px 50px 100px -20px, rgba(0, 0, 0, 0.2) 0px 30px 60px -30px;
  }
</style>
