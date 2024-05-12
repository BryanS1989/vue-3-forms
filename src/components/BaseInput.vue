<template>
    <label :id="uuid">{{ label }}</label>
    <input
        :id="uuid"
        v-bind="$attrs"
        :placeholder="label"
        class="field"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
        :aria-describedby="error ? `${uuid}-error` : null"
    />
    <p v-if="error" class="errorMessage" :id="`${uuid}-error`" aria-live="assertive">
        {{ error }}
    </p>
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
        error: {
            type: String,
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
