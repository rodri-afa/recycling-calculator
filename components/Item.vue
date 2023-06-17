<template>
    <div class="item">
        <label :for="name">{{ labelText }}:</label>
        <div class="input-group">
            <button @click="$emit('increaseBy', -1, item)"> - </button>
            <input type="number" :name="name" step="1" min="0" :value="itemUds"
                @input="$emit('update:itemUds', $event.target.value)">
            <button @click="$emit('increaseBy', 1, item)"> + </button>
        </div>

    </div>
</template>

<script setup>

const props = defineProps(['itemUds', 'name', 'labelText', 'item'])
defineEmits(['update:itemUds', 'increaseBy'])


</script>

<style lang="scss" scoped>
.item {
    display: flex;
    flex-direction: column;
    gap: 4px;
    margin-bottom: 8px;

    .input-group {
        display: flex;
        gap: 8px;

        &>* {
            height: 32px;
            border: 1px solid #aeaeae;
        }

        button {
            font-family: 'ui-sans-serif', san-serif;
            border-radius: 50%;
            width: 34px;
            height: 32px;
            font-weight: 500;
            font-size: 24px;
            display: flex;
            justify-content: center;
            align-items: baseline;
            color: black;

            border &:hover {
                cursor: pointer;
            }
        }

        input[type=number] {
            padding: 0 16px;
            border-radius: 16px;
            width: 88%;

        }
    }
}
</style>