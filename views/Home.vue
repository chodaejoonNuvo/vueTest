<template>
    <div>
        <h1>Welcome to {{title.c}}!</h1>
        <input type="text" value="abc" v-model="input1">
        <button type="button" @click="getData">Get</button>
        <button type="button" @click="setData">Set</button>

        <!-- selectBox -->
        <select class="form-control" v-model="region" @change="changeRegion">
            <!-- [:]:access to variables in Obj, [{{}}]:access to variables on html -->
            <!-- [:key]:is necessary -->
            <option :key="index" :value="data.v" v-for="(data, index) in options">{{data.t}}</option>
        </select>
        <!-- [v-if]:render this Obj on condition -->
        <table class="talbe table-bordered" v-if="talbeShow">
            <tr :key="index" v-for="(data, index) in options">
                <td>{{data.v}}</td>
                <td>{{data.t}}</td>
            </tr>
        </table>
        <!-- [v-show]:render this Obj, but do not show on condition -->
        <table class="talbe table-bordered" v-show="talbeShow">
            <tr :key="index" v-for="(data, index) in options">
                <td>{{data.v}}</td>
                <td>{{data.t}}</td>
            </tr>
        </table>
    </div>

</template>
<script>
export default {

    // declare of data area
    data() {
        return {
            title: {
                a:"Tokyo",
                b:"Seoul",
                c:1},
            title2: "Sydney",
            input1: "Beijing",
            options: [
                {v: "S", t:"Seoul"},
                {v: "N", t:"Newyork"},
                {v: "L", t:"Los Angeles"},
            ],
            region: "L",
            talbeShow: false
        };
    },

    // definition of methods area
    methods: {
        getData() {
            alert(this.input1);
        },
        setData() {
            this.input1 = "12345";
        },
        changeRegion() {
            this.talbeShow = !this.talbeShow;
        }
    },
    // watch definition data altered area
    watch: {

        // create a method with variable name
        input1() {
            console.log(this.input1);
        },
        region() {
            console.log(this.region);
        }
    },

    // overrided methods on lifecycle of Vue.js
    beforeCreate() {
        console.log("beforeCreate");
    },
    created() {
        console.log("created"); 
    },
    beforeMount() {
        console.log("beforeMount");
    },
    mounted() {
        console.log("mounted");
    },
    beforeUpdate() {
        console.log("beforeUpdate");
    },
    updated() {
        console.log("updated");
    },
    beforeDestroy() {
        console.log("beforeDestroy");
    },
    destroyed() {
        console.log("destroyed");
    },
};
</script>