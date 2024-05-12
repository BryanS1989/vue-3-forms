<template>
    <label :id="uuid">{{ label }}</label>
    <input
        :id="uuid"
        v-bind="$attrs"
        :placeholder="label"
        class="field"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
    />
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
