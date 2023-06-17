<template>
    <div>
        <label :for="name">{{ labelText }}:</label><br>
        <div>
            <button @click="$emit('increaseBy', -1, name)"> - </button>
            <input type="number" :name="name" step="1" min="0" :value="itemUds"
                @input="$emit('update:itemUds', $event.target.value)">
            <button @click="$emit('increaseBy', 1, name)"> + </button>
        </div>
    </div>
</template>

<script setup>

const props = defineProps(['itemUds', 'name', 'labelText'])
defineEmits(['update:itemUds', 'increaseBy'])


</script>

<style lang="scss" scoped></style>