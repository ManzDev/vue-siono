<template>
  <div class="box" :style="image">
    <h1>{{ answer }}</h1>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'App',
  data() {
    return {
      answer: '',
      image: {
        backgroundImage: '',
        backgroundSize: 'contain',
        backgroundPosition: 'center',
        backgroundRepeat: 'no-repeat'
      }
    }
  },
  mounted() {
    // fetch('https://yesno.wtf/api')
    //   .then(response => response.json())
    //   .then(response => {
    //     this.answer = response.answer;
    //     this.image.backgroundImage = `url(${response.image})`;
    //   }).catch(e => {
    //     this.answer = '¡ERROR!';
    //     console.error(e);
    //   });
    // OPTION 2: AXIOS */
    axios.get('https://yesno.wtf/api').then(response => {
      this.answer = response.data.answer;
      this.image.backgroundImage = `url(${response.data.image})`;
    }).catch(e => {
      this.answer = '¡ERROR!';
      console.error(e);
    });
  }
}
</script>


<style lang="postcss">
  :root {
    text-align: center;
    background: linear-gradient(130deg, blue, purple);
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .box {
    box-shadow: 5px 5px 15px rgba(0, 0, 0, 0.5);
    background: #111;
    border: 4px solid #000;
    width: 600px;
    height: 400px;
    padding: 8px;
    margin: auto;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    & h1 {
      font-family: Montserrat, Impact, sans-serif;
      font-size: 72px;
      color: #fff;
      text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.75);
      text-transform: uppercase;
    }
  }
</style>
