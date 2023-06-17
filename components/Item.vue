<template>
    <div class="item">
        <label :for="name">{{ labelText }}:</label>
        <div class="input-group">
            <button @click.prevent="$emit('increaseBy', -1, item)"> - </button>
            <input type="tel" :name="name" step="1" min="0" :value="itemUds"
                @input="$emit('update:itemUds', $event.target.value)">
            <button @click.prevent="$emit('increaseBy', 1, item)"> + </button>
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
        justify-content: space-between;
        gap: 8px;

        &>* {
            height: 48px;
            border: 1px solid #aeaeae;
            font-size: 24px;
        }

        button {
            font-family: 'ui-sans-serif', san-serif;
            border-radius: 50%;
            width: 48px;
            font-weight: 500;

            display: flex;
            justify-content: center;
            align-items: center;
            color: black;
            touch-action: manipulation;

            border &:hover {
                cursor: pointer;
            }
        }

        input {
            padding: 0 16px;
            border-radius: 30px;
            width: auto;
            flex: 1;

        }
    }
}
</style>