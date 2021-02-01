<template>
  <div class="home">
    <label for="userText">variable refactoring</label>
    <textarea name="userText" id="userText" cols="30" rows="10" v-on:change="changeItem($event)"></textarea>
    <p class="renderValue">snake_case : {{snake}}</p>
    <p class="renderValue">camelCase : {{camel}}</p>
    <div class="footer">© 2021 - <a href="https://augustinribreau.com" target="_blank">Augustin Ribreau</a></div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  props: {
    snake : String,
    camel : String
  },

  methods: {
    changeItem: function changeItem(event) {
      const _determinant = [
        "mon", "ma", "mes", "ton", "ta", "tes", "son", "sa", "ses", "notre",
        "nos", "de", "votre", "vos" , "leur", "leurs", "le", "la", "les", "des",
        "ces", "'", "/", ",", '"', "`", ")", "(", "&", "§", "!","ç","^", "¨", "$",
        "*","£", "@", "€", "ù", "%", "=", "+", ":", ";", ".", "?", 'the', "i'm"
      ];
      const userValue = event.target.value;
      const _userValues = userValue.split(' ');
      _userValues.filter(value => {
        if (_determinant.includes(value)){
          _userValues.splice(_userValues.indexOf(value), 1);
        }
      });
      this.snake = _userValues.join('_').split("'").join('_');

      function strUcFirst(elem){
        return (elem+'').charAt(0).toUpperCase()+elem.substr(1);
      }

      const camelCaseValues = [];
      _userValues.map((value, index) =>{
        if (index !== 0){
          camelCaseValues.push(strUcFirst(value));
        }else{
          camelCaseValues.push(value);
        }
      })
      this.camel = camelCaseValues.join('');
    }
  }
}

</script>

<style scoped>
.home{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

label{
  font-family: 'Roboto', sans-serif;
  font-size: 70px;
  font-weight: 300;
  margin-bottom: 50px;
  color: darkgreen;
}

textarea {
  background: rgb(242, 242, 242);
  opacity: 0.2;
  color: darkgreen;
  font-family: 'Roboto', sans-serif;
  border: 1px solid black;
  border-radius: 5px;
  padding: 10px;
  font-size: 20px;
  font-weight: 100;
  width: 500px;
  height: 200px;
  resize : none;
  transition: 0.25s;
}

textarea:focus {
  opacity: 1;
  background: white;
  outline: none !important;
  box-shadow: 0 0 10px darkgreen;
  transform: scale(1.1);
}

.renderValue{
  font-family: 'Roboto', sans-serif;
  margin-top: 100px;
  font-size: 30px;
  color: darkgreen;
  font-weight: 200;
}

.footer{
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  padding: 20px 0;
}

.footer a{
  color: darkgreen;
  text-decoration: none;
}
</style>
