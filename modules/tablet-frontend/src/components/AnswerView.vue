<template>
  <div class="answer-view">
    <div class="shadow" :class='["", animation && "animate" ]'><div></div></div>
    <div class="answer" :class='["", animation && "animate" ]'>
      <ul>
        <li v-for="item in answer" :key="item.key">
          <span class="topic">{{ item.topic }}</span>
          <span class="text">{{ item.text }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import config from '../config'
import _isString from 'lodash/isString'

export default {
  name: 'MainView',
  props: ['data'],
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      api: config.apiAddress,
      animation: false
    }
  },
  computed: {
    answer: function () {
      if (!this.data) {
        return []
      }
      return this.data.map((e, i) => {
        return {
          key: i,
          topic: e.topic,
          text: _isString(e.value) ? e.value : e.value.input,
          type: _isString(e.value) ? 'text' : 'choice'
        }
      }, '')
    }
  },
  watch: {
    answer: function () {
      if (this.timeout) {
        this.animation = false
        clearTimeout(this.timeout)
        setTimeout(() => { this.animation = true }, 50)
      } else {
        this.animation = true
      }
      this.timeout = setTimeout(() => { this.animation = false }, 8050)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.answer {
  position: absolute;
  width: 100%;
  max-width: 500px;
  opacity: 0;
  transform: scale(1.0) translate(0, -50%);
  top: 60%;
}

@keyframes drop-down-animation {
  0% { top: 35%; opacity: 0; transform: scale(0.7) translate(0, -50%); }
  10% { top: 60%; opacity: 1; transform: scale(1) translate(0, -50%); }
  95% { top: 60%; opacity: 1; transform: scale(1) translate(0, -50%); }
  100% { top: 63%; opacity: 0; transform: scale(1) translate(0, -50%); }
}

.answer.animate {
  animation: 8s ease-in-out 0s drop-down-animation;
}

ul {
  list-style-type: none;
  padding: 0;
  display: inline
}

li {
  display: block;
  margin: 0 10px;
  text-align: center;
}

@keyframes shadow-animation {
  0% { transform: scale(0.0); opacity: 0 }
  10% { transform: scale(1); opacity: 1 }
  95% { transform: scale(1); opacity: 1 }
  100% { transform: scale(0.9); opacity: 0 }
}

.shadow {
    position: fixed;
    bottom: 0px;
    left:0;
    width: 100%;
    opacity: 0;

}

.shadow > div {
  background: black;
    height: 50px;
    width: 300px;
    max-width: 80%;
    border-radius: 50%;
    -webkit-filter: blur(8px);
    filter: blur(8px);
    opacity: 0.04;
    margin: 50px auto;
}

.shadow.animate {
  transform-origin: center;
  animation: 8s ease-in-out 0s shadow-animation;
}

.topic {
  opacity: 0.2;
  padding-right: 0.5em;
  font-weight: bold;
  /* color: #F8FF00 */
}
</style>
