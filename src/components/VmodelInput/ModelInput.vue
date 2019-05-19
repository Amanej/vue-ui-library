<template>
    <div>
        <input
            v-bind:value="value"
            v-on:blur="saveCurrentValue"
            v-on:keyup.enter="saveInput"
            name="textInput"
            ref="textInput"
        >
        <p>Has changed ? {{changed}}</p>
    </div>
</template>

<script>
export default {
    name: "ModelInput",
    props: {
        value: String, 
    },
    data() {
        return {
            initialValue: ''
        }
    },
    created: function() {
        this.initialValue = this.value;
    },
    computed: {
        changed() {
            return this.initialValue !== this.value
        }
    },
    methods: {
        saveCurrentValue(event) {
            this.initialValue = this.value;
            /***
             * This is to catch the save on blur.
             * @event {Event}
             * @type String
             */
            // this.$emit('input',this.value);
            console.log(' Event ', event, ' Val ',event.target.value);
            this.$emit('input', event.target.value)
        },
        blurInput() {
            this.$refs.textInput.blur();
        },
        saveInput(event) {
            console.log(' Save input ',event);
            this.blurInput();
            this.saveCurrentValue(event);
        },        
    }
}
</script>