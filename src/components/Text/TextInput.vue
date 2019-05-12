<template>
    <label :style="customStyle ? customStyle.label : ''">
        <input 
            :class="{changed: changed}"
            :style="customStyle ? customStyle.input : ''"
            type="text" 
            name="textInput"
            v-on:keyup.enter="saveInput"
            v-on:blur="saveCurrentValue"
            :placeholder="placeholder" 
            v-model="value"
            ref="textInput"
        />
    </label>
</template>

<script>
/* eslint-disable */
/**
 * The text input. Please show me props.
 */
export default {
    name: 'TextInput',
    props: {
        /**
         * Sets the initial value
         */
        initialValue: {
            default: '',
            type: String,
            required: false
        },
        /**
		 * Sets the placeholder
		 */
        placeholder: {
            default: 'Enter your info',
            type: String,
            required: false
        },
        /**
		 * Sets the custom style
		 */
        customStyle: {
            type: Object,
            required: false
        },
        /**
		 * Sets the changed style
		 */
        changedStyle: {
            type: Object,
            required: false
        }
    },
    data: () => {
        return (
            {
                init: '',
                value: ''
            }
        )
    },
    created: function() {
        this.init = this.initialValue;
        this.value = this.initialValue;
    },
    computed: {
        changed() {
            return this.value !== this.init
        }
    },
    methods: {
        saveCurrentValue() {
            this.init = this.value;
            /***
             * This is to catch the save on blur.
             * @event {Event}
             * @type String
             */
            this.$emit('input',this.value);
        },
        blurInput() {
            this.$refs.textInput.blur();
        },
        saveInput() {
            this.blurInput;
            this.saveCurrentValue();
        }
    },
}
</script>

<style lang="scss" scoped>
label {
    //min-width:                  250px;
    transition:                 0.4s;
    width: 100%;
    display: flex;
}
input {
    //padding:                5px;
    font-size:              16px;
    padding:                12px;
    //min-width:              250px;
    width: 100%;
    transition:             0.4s;
    border:                 1px solid lightgrey;
    border-radius: 4px;
    &.changed {
        color: red;
    }
    &:focus {
        outline: none;
    }
}
</style>
