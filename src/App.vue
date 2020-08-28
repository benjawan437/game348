<template>
<div id="app">
    <div class="can">
        <div class="row">
            <div class="col-md-4 col-sm-4">
                <h1>{{go_name}}</h1>
                <b-progress :value="go_hp" :max="g_max" class="bar" show-value variant="succecss"></b-progress>
                <div class="back">
                    <img :src="g_img" class="img-fluid image" :width="go_hp + 'px'" />
                </div>
            </div>
            <div class="col-md-4 mt-5 col-sm-4">
                <img src="./assets/a1.png" />
            </div>
            <div class="col-md-4 col-sm-4">
                <h1>{{ev_name}}</h1>
                <b-progress :value="ev_hp" :max="e_max" class="bar" show-value variant="succecss"></b-progress>
                <div class="back">
                    <img :src=" e_img" class="img-fluid image" :width="ev_hp + 'px'" />
                </div>
            </div>
        </div>
    </div>

    <div class="row">
        <div class="col-md-12 col-sm-12">
            <game @Gname="gname" @Ghp="ghp" @Gimage="gimage" @Ename="ename" @Ehp="ehp" @Eimage="eimage" @Gten="gten" @Eten="eten" @Gwin="gwin" @Ewin="ewin"></game>
        </div>
    </div>
</div>
</template>

<script>
import game from "./components/game";
export default {
    name: "App",
    components: {
        //HelloWorld,
        game,
    },

    data: function () {
        return {
            go_name: "",
            ev_name: "",
            g_max: 0,
            e_max: 0,
            go_hp: 0,
            ev_hp: 0,
            attack: 0,
            g_img: "",
            e_img: "",
        };
    },

    methods: {
        //Good side
        gname(value) {
            this.go_name = value;
        },
        ghp(value) {
            this.go_hp = value;
            this.g_max = value;
        },
        gimage(value) {
            this.g_img = value;
        },
        //Evil side
        ename(value) {
            this.ev_name = value;
        },
        ehp(value) {
            this.ev_hp = value;
            this.e_max = value;
        },
        eimage(value) {
            this.e_img = value;
        },
        //ATTACK Good side
        gten(value) {
            this.attack = value;
            this.ev_hp -= this.attack;
        },
        gwin(value) {
            this.attack = value;
            this.ev_hp -= this.attack;
        },
        //ATTACK Evil side
        eten(value) {
            this.attack = value;
            this.go_hp -= this.attack;
        },
        ewin(value) {
            this.attack = value;
            this.go_hp -= this.attack;
        },
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #313030;
}

.can {
    margin: auto;
    width: 90%;
    height: 600px;
}

.gvse {
    margin-top: 20vw;
}

.back {
    display: inline-block;
    margin: 5px;
    bottom: 0;
}
</style>
