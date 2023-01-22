<template>
  <div class="allGame">
    <span style="font: 17px monospace; font-weight: 900"
      >Крестики - нолики</span
    >
    <br />
    <br />
    <div v-if="show == false">
      <span>Кем будете ходить ?</span>
      <br />
      <br />
      <div style="display: flex; justify-content: center">
        <div class="player" id="player1" @click="getPlayer('X')">X</div>
        <span
          style="
            font: 40px monospace;
            text-align: center;
            padding: 0 15px 0 15px;
          "
        >
          /
        </span>
        <div class="player" id="player2" @click="getPlayer('O')">O</div>
      </div>
    </div>
    <div v-if="show == true">Ход игрока '{{ player }}'</div>
    <br />
    <div>
      <div class="block" @change="watchChange">
        <div class="all">
          <div class="field" id="n1" @click="setPlayer('n1')"></div>
          <div class="field" id="n2" @click="setPlayer('n2')"></div>
          <div class="field" id="n3" @click="setPlayer('n3')"></div>
        </div>
        <div class="all">
          <div class="field" id="n4" @click="setPlayer('n4')"></div>
          <div class="field" id="n5" @click="setPlayer('n5')"></div>
          <div class="field" id="n6" @click="setPlayer('n6')"></div>
        </div>
        <div class="all">
          <div class="field" id="n7" @click="setPlayer('n7')"></div>
          <div class="field" id="n8" @click="setPlayer('n8')"></div>
          <div class="field" id="n9" @click="setPlayer('n9')"></div>
        </div>
      </div>
    </div>
    <button style="margin: 20px" @click="reset">Сброс</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      player: '',
      show: false,
    };
  },
  mounted() {},
  computed: {},
  methods: {
    getPlayer(name) {
      if (name === 'X') this.player = 'X';
      else this.player = 'O';
      this.show = true;
    },
    setPlayer(id) {
      document.getElementById(id).innerHTML = this.player;
      if (this.player == 'X') {
        this.player = 'O';
      } else this.player = 'X';
    },
    reset() {
      for (let i = 1; i < 10; i++) {
        document.getElementById(`n${i}`).innerHTML = '';
      }
      this.show = false;
    },
    watchChange(event) {
      console.log(event);
    },
  },
};
</script>

<style scoped>
.allGame {
  box-shadow: 15px 10px 30px #000;
  padding: 50px;
  width: 165px;
  height: 310px;
  border: 5px solid;
  border-radius: 15px;
}
.player {
  border-radius: 10px;
  border: 1px solid;
  width: 50px;
  height: 50px;
  font: 40px monospace;
  text-align: center;
}
input {
  font: 40px monospace;
  display: flex;
  justify-content: center;
  justify-items: center;
  text-align: center;
}
.block {
  border-radius: 15px;
  border: 5px solid orange;
}
.all {
  display: flex;
}
.field {
  font: 40px monospace;
  border-radius: 10px;
  border: 1px solid;
  width: 50px;
  height: 50px;
}
</style>
