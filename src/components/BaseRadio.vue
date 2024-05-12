<template>
    <input
        :id="uuid"
        type="radio"
        :checked="modelValue === value"
        :value="value"
        @change="$emit('update:modelValue', value)"
        v-bind="$attrs"
    />
    <label v-if="label" :id="uuid">{{ label }}</label>
</template>

<script>
import UniqueID from '@/helper/UniqueId.js';

export default {
    props: {
        label: {
            type: String,
            default: ''
        },
        modelValue: {
            type: [String, Number],
            default: ''
        },
        value: {
            type: [String, Number],
            required: true
        }
    },
    setup() {
        const uuid = UniqueID().getID();
        return {
            uuid
        };
    }
};
</script>
