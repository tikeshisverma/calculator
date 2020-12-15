<template>
  <div id="app">
    <div class="cal-container">
      <div class="display">
        {{ textContent }}
      </div>
      <div class="button-container" @click="number">
        <div class="number-container">
          <div class="wrapper-1">
          <button data-value="1">1</button>
          <button data-value="2">2</button>
          <button data-value="3">3</button>
          </div>
          <div class="wrapper-2">
          <button data-value="4">4</button>
          <button data-value="5">5</button>
          <button data-value="6">6</button>
          </div>
          <div class="wrapper-3">
          <button data-value="7">7</button>
          <button data-value="8">8</button>
          <button data-value="9">9</button>
          </div>
          <div class="wrapper-4">
          <button data-value="0">0</button>
        <button @click="clr">C</button>
</div>
        <button @click="equal" class="equal">=</button>

        </div>
        <div class="cal-button">
          <button @click="del">D</button>

          <button data-value="+">+</button>
          <button data-value="-">-</button>
          <button data-value="*">*</button>
          <button data-value="/">/</button>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      textContent: "",
      array: [],
      a: "",
      b: "",
    };
  },
  methods: {
    number(e) {
      console.log("from number", this.textContent);
      this.array.push(e.target.dataset.value);
      this.textContent = `${this.array.join("")}`;
    },
    del(e){
      this.array.pop()
      this.textContent = `${this.array.join("")}`;
 e.stopPropagation()
    },
    clr(e){
      this.textContent=""
      this.array= []
      console.log(this.textContent)
      e.stopPropagation()
    },
    equal(e) {
      if(this.textContent.includes("+")){
      let c = this.textContent.split("+");
      this.textContent = parseInt(c[0]) + parseInt(c[1]); 
      }//NaN
     
else  if(this.textContent.includes("-")){
      let d = this.textContent.split("-");
      this.textContent = parseInt(d[0]) - parseInt(d[1]);
}

else  if(this.textContent.includes("*")){
      let e = this.textContent.split("*");
      this.textContent = parseInt(e[0]) * parseInt(e[1]);
}

else  if(this.textContent.includes("/")){
      let f = this.textContent.split("/");
      this.textContent = parseInt(f[0]) / parseInt(f[1]);
}

      e.stopPropagation();
    },
  },
};
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Lobster&display=swap');
html,body{
  height: 100%
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
}
.cal-container{
    display: flex;
    flex-direction: column;
height: 100%;
    align-items: center;
    justify-content: center;
    box-shadow: 0 15px 30px 5px rgba(0, 0, 0, 0.3);


}
.cal-button button{
  width: 100%;
}
.wrapper-4 button{
  width:50%
  }
.button-container{
  display:flex;
flex-direction: row;
width: 30%;
    height: 30%;
    border: solid;
    box-shadow: 0 15px 30px 5px rgba(0, 0, 0, 0.3);
border-radius: 3%;
}
.number-container{
  display: flex;
  flex-direction: column;
  width: 100%;
  
}
button{
  font-family: 'Lobster', cursive;
  height: 100%;
  width: 33%;
  font-size: large;

}
.display{
  font-family: 'Lobster', cursive;
  border: solid;
  width: 30%;
  height: 5%;
  display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 10%;
    box-shadow: 0 15px 30px 5px rgba(0, 0, 0, 0.3);


}
.equal{
  height: 20%;
  width: 100%;
}
.wrapper-1{
  height: 20%;
}
.wrapper-2{
  height: 20%;
}
.wrapper-3{
  height: 20%;
}
.wrapper-4{
  height: 20%;
}

.cal-button{
  display: flex;
  flex-direction: column;
  width: 20%;
}
</style>
