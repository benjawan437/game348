<template>
  <div>

    {{player[randomNO(1,3)-1].name}}<br><br>
    <!--ได้ทั้งชื่อและ hp ออกมา-->
    <!--{{randomDamage(1,300)}} สุ่ม 1 - 300-->
    <button v-on:click="$start" class="button-a" id="yellow">START</button>
    <button v-on:click="$attack" class="button-a" id="purple">ATTACH</button>
    <hr />
    name = {{aPlayer.name}}
    hp = {{aPlayer.hp}}
    image = {{aPlayer.image}}
    <hr />
    name = {{bMonster.name}}
    hp = {{bMonster.hp}}
    image = {{bMonster.image}}

  </div>
</template>

<script>
export default {
  data: function () {
    return {
      //เอาชื่อออกจาก object player[1].name
      //เอาชื่อออกจาก object player[random].name
      aPlayer: { name: "", hp: 0, image: "" },
      bMonster: { name: "", hp: 0, image: "" },
      attack: 0,
      special: 0,
      player: [
        { name: "SM", hp: 160, image: "a" },
        { name: "JYP", hp: 90, image: "b" },
        { name: "YG", hp: 115, image: "c" },
        { name: "BIGHIT", hp: 145, image: "d" },
      ],
      monster: [
        { name: "Sasaengs", hp: 90, image: "x" },
        { name: "Fanclub", hp: 110, image: "y" },
        { name: "Dispatch", hp: 125, image: "z" },
        { name: "Idol", hp: 150, image: "v" },
      ],
    };
  },
  methods: {
    randomNO: function (min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },
    $start: function () {
      //1.random Plaryer 1-3 -->ชื่อ ค่า hp รูป ฝากไว้ใน aPlary
      this.aPlayer = this.player[this.randomNO(1, 4) - 1];
      this.bMonster = this.monster[this.randomNO(1, 4) - 1];
      //2.random Monster 1-3
    },
    $attack: function () {
        // p -> mon
        // p <- mon
        //p <=0 ===ทำไง  you lose
        //mon <==0 ทำไง you win
        //End


    },
    $special: function () {},
  },
};
</script>
<style scoped>
.b {
  font-size: 50px;
}
.button-a {
  background-color: rgb(80, 79, 79);
  border: none;
  padding: 5px 5px 5px 5px;
  text-align: center;
  display: inline-block;
  margin: 4px 2px;
  font-size: 50px;
  cursor: pointer;
  border-radius: 10px;
  border: 0.5px solid white;
  width: 300px;
}
.button-a-font-dd {
  background-color: rgb(250, 223, 103);
  border: none;
  color: #d32c2c;
  padding: 5px 5px 5px 5px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  margin: 4px 2px;
  cursor: pointer;
  border-radius: 10px;
  border: 0.5px solid #ffffff;
  width: 300px;
}
button:hover#yellow {
  color: #f70000;
}
button:hover#purple {
  color: #1df700;
}
</style>