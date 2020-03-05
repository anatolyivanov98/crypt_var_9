<template>
  <div class="home">
    <div class="main">
      <div class="encrypt">
        <input type="text" placeholder="Начальное слово" v-model="firstWorld">
        <input type="text" placeholder="Зашифрованное слово" v-model="secondWorld">
        <button @click.prevent="encrypt">Зашифровать</button>
      </div>
      <div class="decrypt">
        <input type="text" placeholder="Зашифрованное слово" v-model="encryptWorld">
        <input type="text" placeholder="Расшифрованное слово" v-model="decryptWorld">
        <button @click.prevent="decrypt">Расшифровать</button>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Home',
  data:() => ({
    firstWorld: '',
    secondWorld: '',
    encryptWorld: '',
    decryptWorld: '',
    array: ['а', 'б', 'в', 'г' ,'д', 'е', 'ё', 'ж', 'з', 'и', 'й', 'к', 'л', 'м', 'н', 'о', 'п', 'р', 'с', 'т',
      'у', 'ф', 'х', 'ц', 'ч', 'ш', 'щ', 'ъ', 'ы', 'ь', 'э', 'ю', 'я'],
    firstArr: ['щ', 'о', 'й', 'я', 'р', 'г', 'у', 'д', 'ь', 'и', 'а', 'л', 'ш', 'ё', 'ъ', 'к', 'т', 'е', 'з', 'п', 'с',
      'ы', 'в', 'ж', 'м', 'э', 'ю', 'ф', 'н', 'ч', 'ц', 'б', 'х'],
    secondArr: ['в', 'ц', 'р', 'й', 'ы', 'у', 'ё', 'г', 'ш', 'м', 'о', 'ф', 'ч', 'а', 'д', 'э', 'п', 'ж', 'и', 'т', 'н',
      'е', 'я', 'х', 'к', 'б', 'ъ', 'с', 'ь', 'щ', 'ю', 'л', 'з']
  }),
  methods: {
    encrypt() {
      const arr1 = this.firstWorld.split('')
      const arr2 = []

      for (let i = 0; i < arr1.length; i++) {
        for (let j = 0; j < this.array.length; j++) {
          if (arr1[i] === this.array[j]) {
            if (i%2 === 0) {
              arr2.push(this.firstArr[j])
            } else {
              arr2.push(this.secondArr[j])
            }
          }
        }
      }
      this.secondWorld = arr2.join('')
      this.encryptWorld = this.secondWorld
      this.decryptWorld = ''
    },
    decrypt() {
      const arr1 = this.encryptWorld.split('')
      const arr2 = []

      for (let i = 0; i < arr1.length; i++) {
        for (let j = 0; j < this.array.length; j++) {
            if (i%2 === 0) {
              if (arr1[i] === this.firstArr[j]) {
                arr2.push(this.array[j])
              }
            } else if(arr1[i] === this.secondArr[j]) {
              arr2.push(this.array[j])
            }
        }
      }

      this.decryptWorld = arr2.join('')
    }
  }
}
</script>

<style lang="scss" scoped>
  .home{
    display: flex;
    justify-content: center;
    padding-top: 200px;

    .main {
      display: flex;

      input {
        border: none;
        border-bottom: 2px solid #999999;
        width: 200px;
        margin: 5px auto;
      }

      input:focus {
        outline: none;
      }

      button {
        width: 150px;
        margin: 10px auto;
        color: #5b5b5b;
        background: white;
        border: 1px solid #999999;
        border-radius: 5px;
        padding: 2px 0;
        cursor: pointer;
      }

      .encrypt {
        display: flex;
        flex-direction: column;
        margin-right: 15px;
        width: 300px;
        justify-content: center;
        padding: 10px 0 5px 0;
        box-shadow: 1px 1px 10px rgba(153, 153, 153, 0.8);
      }

      .decrypt{
        display: flex;
        flex-direction: column;
        margin-left: 15px;
        width: 300px;
        padding: 10px 0 5px 0;
        box-shadow: 1px 1px 10px rgba(153, 153, 153, 0.8);
      }
    }
  }
</style>
