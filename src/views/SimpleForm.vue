<template>
    <div>
        <h1>Create an event</h1>
        <form @submit.prevent="sendForm">
            <BaseSelect :options="categories" v-model="event.category" label="Select a category" />

            <fieldset>
                <legend>Name & describe your event</legend>

                <BaseInput v-model="event.title" label="Title" type="text" />

                <BaseInput v-model="event.description" label="Description" type="text" />
            </fieldset>

            <fieldset>
                <legend>Where is your event?</legend>

                <BaseInput v-model="event.location" label="Location" type="text" />
            </fieldset>

            <fieldset>
                <legend>Pets</legend>

                <p>Are pets allowed?</p>

                <div>
                    <BaseRadioGroup
                        v-model="event.pets"
                        name="pets"
                        :options="petOptions"
                        vertical
                    />
                </div>
            </fieldset>

            <fieldset>
                <legend>Extras</legend>

                <div>
                    <BaseCheckbox v-model="event.extras.catering" label="Catering" />
                </div>

                <div>
                    <BaseCheckbox v-model="event.extras.music" label="Live music" />
                </div>
            </fieldset>

            <button class="button -fill-gradient" type="submit">Submit</button>
        </form>
    </div>
</template>

<script>
import axios from 'axios';

import BaseInput from '@/components/BaseInput.vue';
import BaseSelect from '@/components/BaseSelect.vue';
import BaseCheckbox from '@/components/BaseCheckbox.vue';
import BaseRadioGroup from '@/components/BaseRadioGroup.vue';

export default {
    data() {
        return {
            categories: [
                'sustainability',
                'nature',
                'animal welfare',
                'housing',
                'education',
                'food',
                'community'
            ],
            event: {
                category: '',
                title: '',
                description: '',
                location: '',
                pets: 1,
                extras: {
                    catering: false,
                    music: false
                }
            },
            petOptions: [
                { label: 'Yes', value: 1 },
                { label: 'No', value: 0 }
            ]
        };
    },
    components: {
        BaseInput,
        BaseSelect,
        BaseCheckbox,
        BaseRadioGroup
    },
    methods: {
        sendForm() {
            console.log('Form submitted');
            axios
                .post(
                    'https://my-json-server.typicode.com/BryanS1989/vue-3-forms/events',
                    this.event
                )
                .then((response) => {
                    console.log(response);
                })
                .catch((err) => {
                    console.log(err);
                });
        }
    }
};
</script>

<style>
fieldset {
    border: 0;
    margin: 0;
    padding: 0;
}

legend {
    font-size: 2rem;
    font-weight: bold;
    margin-top: 2rem;
}
</style>
