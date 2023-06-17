<template>
    <main>
        <h1>Recycling Calculator ♻️</h1>
        <h2>Total: <b>${{ total }} CAD</b></h2>
        <!-- <fieldset>
            <legend>🥫 Cans</legend>
            <label for="smallCan">Small Cans:</label> <br>
            <div>
                <button @click="objects.smallCan.uds--"> - </button>
                <input type="number" name="smallCan" id="smallCan" step="1" min="0" v-model="objects.smallCan.uds">
                <button @click="objects.smallCan.uds++"> + </button>
            </div>

            <label for="bigCan">Big Cans:</label><br>
            <div>
                <button @click="objects.bigCan.uds--"> - </button>
                <input type="number" name="bigCan" id="bigCan" step="1" min="0" v-model="objects.bigCan.uds">
                <button @click="objects.bigCan.uds++"> + </button>
            </div>
        </fieldset>

        <fieldset>
            <legend>🍾 Bottles</legend>
            <label for="smallPlasticBottle">Small Plastic Bottle:</label><br>
            <div>
                <button @click="objects.smallPlasticBottle.uds--"> - </button>
                <input type="number" name="smallPlasticBottle" id="smallPlasticBottle" step="1" min="0"
                    v-model="objects.smallPlasticBottle.uds">
                <button @click="objects.smallPlasticBottle.uds++"> + </button>
            </div>
            <label for="bigPlasticBottle">Big Plastic Bottle:</label><br>
            <div>
                <button @click="objects.bigPlasticBottle.uds--"> - </button>
                <input type="number" name="bigPlasticBottle" id="bigPlasticBottle" step="1" min="0"
                    v-model="objects.bigPlasticBottle.uds">
                <button @click="objects.bigPlasticBottle.uds++"> + </button>
            </div>
            <label for="crystalBottle">Crystal Bottle:</label><br>
            <div>
                <button @click="objects.crystalBottle.uds--"> - </button>
                <input type="number" name="crystalBottle" id="crystalBottle" step="1" min="0"
                    v-model="objects.crystalBottle.uds">
                <button @click="objects.crystalBottle.uds++"> + </button>
            </div>
        </fieldset> -->

        <p>Quebec recycling system</p>

        <Item v-for="o, key in objects" :labelText="o.labelText" :name="key" v-model:itemUds="o.uds"
            @increase-by="increaseUds">
        </Item>

    </main>
</template>

<script setup>
import { reactive, computed } from 'vue'



const objects = reactive({
    smallCan: {
        labelText: "Small Cans",
        uds: 0,
        price: 0.05
    },
    bigCan: {
        labelText: "Big Cans",
        uds: 0,
        price: 0.2
    },
    smallPlasticBottle: {
        labelText: "Small Plastic Bottle",
        uds: 0,
        price: 0.05
    },
    bigPlasticBottle: {
        labelText: "Small Plastic Bottle",
        uds: 0,
        price: 0.05
    },
    crystalBottle: {
        labelText: "Crystal Bottle",
        uds: 0,
        price: 0.1
    },
})

function increaseUds(amount, name) {
    if (objects[name].uds === 0 && amount === -1) {
        objects[name].uds = 0
    } else {
        objects[name].uds = Number(objects[name].uds) + amount
    }


}

const total = computed(() => {
    let sum = 0

    for (let o in objects) {
        sum = sum + objects[o]['uds'] * objects[o]['price']
    }
    console.log(sum)
    return sum.toFixed(2)
})


</script>
