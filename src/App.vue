<template>
  <div id="app">
    <div class="box">
      <div class="card" :class="{circle: value === 'O', error: value === 'X'}" @click="set(key)" v-for="(value,key)  in numbers" :key="key">{{value}}</div>
    </div>
    <button @click="reset">Restart!!!</button>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      numbers: {
        one: "",
        two: "",
        three: "",
        four: "",
        five: "",
        six: "",
        seven: "",
        eight: "",
        nine: ""
      },
      circle: true,
      over: false
    };
  },
  methods: {
    set(index) {
      if (this.numbers[index] === "" && this.over === false) {
        if (this.circle === true) {
          this.numbers[index] = "O";
        } else {
          this.numbers[index] = "X";
        }
        this.circle = !this.circle;
      }
    },
    checkWin() {
      console.log(this.numbers.one);
      let vm = this;
      if (
        vm.numbers.one !== "" &&
        vm.numbers.one === vm.numbers.two &&
        vm.numbers.two === vm.numbers.three &&
        vm.numbers.one === vm.numbers.three
      ) {
        vm.showResult(vm.numbers.one);
      } else if (
        vm.numbers.four !== "" &&
        vm.numbers.four === vm.numbers.five &&
        vm.numbers.five === vm.numbers.six &&
        vm.numbers.four === vm.numbers.six
      ) {
        vm.showResult(vm.numbers.four);
      } else if (
        vm.numbers.seven !== "" &&
        vm.numbers.seven === vm.numbers.eight &&
        vm.numbers.eight === vm.numbers.nine &&
        vm.numbers.seven === vm.numbers.nine
      ) {
        vm.showResult(vm.numbers.seven);
      } else if (
        vm.numbers.one !== "" &&
        vm.numbers.one === vm.numbers.four &&
        vm.numbers.four === vm.numbers.seven &&
        vm.numbers.one === vm.numbers.seven
      ) {
        vm.showResult(vm.numbers.one);
      } else if (
        vm.numbers.two !== "" &&
        vm.numbers.two === vm.numbers.eight &&
        vm.numbers.eight === vm.numbers.five &&
        vm.numbers.two === vm.numbers.five
      ) {
        vm.showResult(vm.numbers.two);
      } else if (
        vm.numbers.three !== "" &&
        vm.numbers.three === vm.numbers.six &&
        vm.numbers.six === vm.numbers.nine &&
        vm.numbers.three === vm.numbers.nine
      ) {
        vm.showResult(vm.numbers.three);
      } else if (
        vm.numbers.one !== "" &&
        vm.numbers.one === vm.numbers.nine &&
        vm.numbers.nine === vm.numbers.five &&
        vm.numbers.one === vm.numbers.five
      ) {
        vm.showResult(vm.numbers.one);
      } else if (
        vm.numbers.three !== "" &&
        vm.numbers.three === vm.numbers.five &&
        vm.numbers.five === vm.numbers.seven &&
        vm.numbers.three === vm.numbers.seven
      ) {
        vm.showResult(vm.numbers.three);
      } else if (
        vm.numbers.one !== "" &&
        vm.numbers.two !== "" &&
        vm.numbers.three !== "" &&
        vm.numbers.four !== "" &&
        vm.numbers.five !== "" &&
        vm.numbers.six !== "" &&
        vm.numbers.seven !== "" &&
        vm.numbers.eight !== "" &&
        vm.numbers.nine !== ""
      ) {
        setTimeout(() => {
          window.alert(`竟然平手啦！！！`);
          vm.over = true;
        }, 250);
      }
    },
    showResult(symbal) {
      let vm = this;
      setTimeout(() => {
        window.alert(`${symbal} Win!!`);
        vm.over = true;
      }, 250);
    },
    reset() {
      this.numbers = {
        one: "",
        two: "",
        three: "",
        four: "",
        five: "",
        six: "",
        seven: "",
        eight: "",
        nine: ""
      };
      this.over = false;
    }
  },
  updated() {
    this.checkWin();
  }
};
</script>

<style>
.box {
  width: 350px;
  height: 350px;
  margin: 0 auto;
  border: 1px solid black;
  padding: 25px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

.card {
  width: 100px;
  height: 100px;
  border: 1px solid black;
  font-size: 4rem;
  background-color: #ffffff;
  color: #1d1d1d;
  transition: background-color 0.25s linear, color 0.25s linear;
  display: flex;
  justify-content: center;
  align-items: center;
}

.card.circle {
  background-color: #4fa0da;
  color: #ffffff;
  transition: background-color 0.25s linear, color 0.25s linear;
}

.card.error {
  background-color: #da4f4f;
  color: #ffffff;
  transition: background-color 0.25s linear, color 0.25s linear;
}

button {
  display: block;
  padding: 5px 10px;
  border: 1px solid black;
  margin: 10px auto;
}
</style>
