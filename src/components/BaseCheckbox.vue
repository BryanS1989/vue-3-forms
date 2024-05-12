<template>
    <input
        :id="uuid"
        type="checkbox"
        :checked="modelValue"
        class="field"
        @change="$emit('update:modelValue', $event.target.checked)"
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
            type: Boolean,
            default: false
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
