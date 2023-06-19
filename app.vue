<template>
    <main>
        <h1>♻️ Recycling Calculator </h1>
        <!-- <p>Quebec recycling system</p> -->

        <div class="card">
            <h2 class="title">total</h2>
            <h2 class="amount"> ${{ total }} CAD</h2>

            <button id="reset-button" @click="reset">
                <Icon name="ph:arrows-counter-clockwise" size="24" />
            </button>


            <fieldset>
                <legend>Cans</legend>
                <Item v-for="c, key in cans" :labelText="c.labelText" :name="key" :item="c" v-model:itemUds="c.uds"
                    @increase-by="increaseUds">
                </Item>
            </fieldset>
            <fieldset>
                <legend>Bottles</legend>
                <Item v-for="b, key in bottles" :labelText="b.labelText" :name="key" :item="b" v-model:itemUds="b.uds"
                    @increase-by="increaseUds">
                </Item>
            </fieldset>
        </div>

    </main>
</template>

<script setup>
import { reactive, computed } from 'vue'



const cans = reactive({
    smallCan: {
        labelText: "Small Cans",
        uds: 0,
        price: 0.05
    },
    bigCan: {
        labelText: "Big Cans",
        uds: 0,
        price: 0.2
    }
})
const bottles = reactive({
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

function increaseUds(amount, item) {
    if (item.uds === 0 && amount === -1) {
        item.uds = 0
    } else {
        item.uds = Number(item.uds) + amount
    }
    // console.log(amount, item);

}

const total = computed(() => {
    let sum = 0

    for (let c in cans) {
        sum = sum + cans[c]['uds'] * cans[c]['price']
    }
    for (let b in bottles) {
        sum = sum + bottles[b]['uds'] * bottles[b]['price']
    }
    // console.log(sum)
    return sum.toFixed(2)
})

function reset() {
    console.log('reset')
    for (let c in cans) {
        cans[c]['uds'] = 0
    }
    for (let b in bottles) {
        bottles[b]['uds'] = 0
    }
}

</script>

<style scoped lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Fraunces:wght@400;600;800&family=Raleway:wght@400;500;700&display=swap');

main {
    padding-top: 12px;
}

h1 {
    font-size: 28px;
    text-align: center;
}


h2 {
    &.title {
        font-family: 'Raleway', sans-serif;
        font-size: 10px;
        text-decoration: underline;
        text-transform: uppercase;
        margin-bottom: 8px;
    }

    &.amount {
        font-size: 20px;
        margin-bottom: 12px;
    }

    text-align: center;

}

.card {
    min-height: 90vh;
    padding: 12px;
    background-color: white;
    border-radius: 24px 24px 0 0;
    filter: drop-shadow(0 0 8px rgba(0, 0, 0, 0.3));
    margin-top: 24px;
    position: relative;
}

fieldset {
    padding: 12px;
    border-radius: 12px;
    margin-bottom: 24px;

    legend {
        margin-left: 12px;
        padding: 0 8px;
        text-transform: uppercase;
        font-family: 'Raleway', sans-serif;
        font-size: 12px;
        font-weight: 600;
    }

    &:last-of-type {
        margin-bottom: 0;
    }
}

#reset-button {
    background: transparent;
    color: #aeaeae;
    border: 1px solid #aeaeae;
    width: 48px;
    height: 48px;
    border-radius: 50%;
    position: absolute;
    top: 16px;
    right: 16px;


    &:hover {
        color: black;
        border: 1px solid black;
        cursor: pointer;

    }
}
</style>