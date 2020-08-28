<template>
<div id="app">
    <div class="can">
        <div class="row">
            <div class="col-md-4 col-sm-4">
                <h1>{{go_name}}</h1>
                <h3>HP: {{go_hp}}</h3>
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
                <h3>HP: {{ev_hp}}</h3>
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

            <pop v-if="go_hp <= 0 && ev_hp > 0 && go_name != ''" @$reset="$reset" @reset="reset" @close="showModal = false">
                <h1 slot="body">YOU LOUSE</h1>
            </pop>
            <pop v-if="ev_hp <= 0 && go_hp > 0 && go_name != ''" @$reset="$reset" @reset="reset" @close="showModal = false">
                <h1 slot="body">YOU WIN</h1>
            </pop>
            <pop v-if="(go_hp<=0 && ev_hp <= 0 ) && go_name != ''" v-bind="reset" @$reset="$reset" @reset="reset" @close="showModal = false">
                <h1 slot="body">DRAW</h1>
            </pop>
        </div>
    </div>
</div>
</template>

<script>
import game from "./components/game";
import pop from "./components/pop";
export default {
    name: "App",
    components: {
        game,
        pop,
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
        $reset(value) {
            this.go_name = value;
            this.ev_name = value;
            this.g_img = value;
            this.e_img = value;
        },
        reset(value) {
            this.go_hp = value;
            this.ev_hp = value;
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
    color: #020202;
}

.can {
    margin: auto;
    width: 90%;
    height: 600px;
}

.gvse {
    margin-top: 30vw;
}

.tiles {
    position: absolute;
    bottom: 5%;
    width: 100%;
}

.back {
    display: inline-block;
    margin: 5px;
    bottom: 0;
}
</style>
