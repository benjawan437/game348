<template>
<div>
    <!--ได้ทั้งชื่อและ hp ออกมา-->
    <!--{{randomDamage(1,300)}} สุ่ม 1 - 300-->
    <button v-on:click="$start" class="button-a" id="start">START</button>
    <button v-on:click="$attack" class="button-a" id="ten">ATTACH</button>
    <button v-on:click="$attack" class="button-a" id="ten">SPECIAL ATTACH</button>

</div>
</template>

<script>
export default {
    data: function () {
        return {
            //เอาชื่อออกจาก object player[1].name
            //เอาชื่อออกจาก object player[random].name
            player: [{
                    name: "Levi",
                    hp: 260,
                    image: require("../assets/1.png"),
                },
                {
                    name: "Eren Titan",
                    hp: 210,
                    image: require("../assets/4.png"),
                },
                {
                    name: "Armin",
                    hp: 110,
                    image: require("../assets/3.png"),
                },
                {
                    name: "Mikasa",
                    hp: 230,
                    image: require("../assets/2.png"),
                },
                {
                    name: "Jean",
                    hp: 120,
                    image: require("../assets/5.png"),
                },
            ],

            monster: [{
                    name: "Colossal Titan",
                    hp: 210,
                    image: require("../assets/11.png"),
                },
                {
                    name: "Armored Titan",
                    hp: 230,
                    image: require("../assets/13.png"),
                },
                {
                    name: "Beast Titan",
                    hp: 255,
                    image: require("../assets/14.png"),
                },
                {
                    name: "Female Titan",
                    hp: 190,
                    image: require("../assets/12.png"),
                },
                {
                    name: "Annie",
                    hp: 120,
                    image: require("../assets/15.png"),
                },
            ],
        };
    },
    methods: {
        randomNO: function (min, max) {
            return Math.max(Math.floor(Math.random() * max) + 1, min);
        },
        $start: function () {
            this.plaran = this.randomNO(1, 5) - 1;
            this.monran = this.randomNO(1, 5) - 1;
            //1.random Plaryer 1-3 -->ชื่อ ค่า hp รูป ฝากไว้ใน aPlary
            this.nameP1 = this.player[this.plaran].name;
            this.$emit("Gname", this.nameP1);
            console.log("emit", this.nameP1);
            this.hpp1 = this.player[this.plaran].hp;
            this.$emit("Ghp", this.hpp1);
            console.log("hp", this.hpp1);
            this.imag1 = this.player[this.plaran].image;
            this.$emit("Gimage", this.imag1);
            console.log("ima", this.imag1);
            //2.random Monster 1-3
            this.nameM2 = this.monster[this.monran].name;
            console.log("emit", this.nameM2);
            this.$emit("Ename", this.nameM2);
            this.hpM2 = this.monster[this.monran].hp;
            this.$emit("Ehp", this.hpM2);
            this.imagM2 = this.monster[this.monran].image;
            this.$emit("Eimage", this.imagM2);
        },
        $attack: function () {
            this.ten = this.randomNO(3, 10);
            this.$emit("Gten", this.ten);
            console.log("attack", this.nameM2);

            this.ten = this.randomNO(3, 10);
            this.$emit("Eten", this.ten);
            console.log("atte", this.nameM2);

        },
        $special: function () {
            this.sa = this.randomNO(10, 20);
            this.$emit("Gwin", this.sa);
            console.log("sattag", this.nameM2);

            this.sa = this.randomNO(10, 20);
            this.$emit("Ewin", this.sa);
            console.log("satte", this.nameM2);

        },
    },
};
</script>

<style scoped>
.b {
    font-size: 50px;
}

.button-a {
    background-color: rgba(49, 49, 49, 0.8);
    border: none;
    padding: 5px 5px 5px 5px;
    text-align: center;
    display: inline-block;
    margin: 4px 2px;
    font-size: 30px;
    cursor: pointer;
    border-radius: 10px;
    border: 0.5px solid rgb(43, 43, 43);
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

button:hover#num1 {
    color: #76ff26;
}

button:hover#num2 {
    color: #ff2b2b;
}

button:hover#num3 {
    color: #fffc34;
}
</style>
