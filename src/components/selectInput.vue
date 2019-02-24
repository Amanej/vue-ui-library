<template>
    <div class="selectInput" :class="{open: open}">
        <div class="selected" @click="toggleSelect"> <!-- Selected container -->
            <span v-if="!selectedOpt">Select an option</span>
            <span v-if="selectedOpt">{{selectedOpt.label}}</span>
            <label for="toggleSelect">
                <i :class="{open: open}"><</i><!-- icon -->
                <input type="checkbox" v-model="open" id="toggleSelect" name="toggleSelect" />
            </label>
        </div>
        <ul class="options"> <!-- Options -->
            <li v-for="option in options" :key="option.key" @click="setSelectedOption(option)">
                {{option.label}}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'selectInput',
    computed: {
        selectedOption() {
            return this.options.find(o => o.selected)
        }
    },
    methods: {
        setSelectedOption(opt) {
            this.selectedOpt = opt;
            this.open = false;
        },
        toggleSelect() {
            this.open = !this.open;
        }
    },
    data() {
        return {
            open: false,
            selectedOpt: null,
            options: [
                {
                    label: 'Option 1',
                    key: 'opt1',
                    selected: false
                },
                {
                    label: 'Option 2',
                    key: 'opt2',
                    selected: false
                },
                {
                    label: 'Option 3',
                    key: 'opt3',
                    selected: false
                },
                {
                    label: 'Option 4',
                    key: 'opt4',
                    selected: false
                }
            ]
        }
    }
}
</script>

<style lang="scss" scoped>
div.selectInput {
    width: 100%;

    display: flex;
    align-items: flex-start;
    flex-wrap: wrap;

    div.selected {
        border:             1px solid lightgrey;
        padding:            10px;
        display:            flex;
        width: 100%;
        justify-content:    center;
        cursor:             pointer;
        span {
            padding-left:   10px;
        }
        label {
            margin-left:    auto;
            cursor: pointer;
            i {
                font-style:     normal;
                color:          lightgrey;
                display: block;
                transition: 1s;
                &.open {
                    transform: rotate(-90deg);
                }
            }
            input[type="checkbox"] {
                display: none;
            }
        }
    }
    ul.options {
        list-style-type:    none;
        padding:            0;
        width:              100%;
        flex-direction:     column;
        text-align:         left;
        border:             1px solid lightgrey;
        margin:             0;
        display:            none;
        li {
            padding:                5px 10px;
            border-bottom:          1px solid lightgrey;
            cursor:                 pointer;
            &:first-child {
                border-top:         none;                
            }
            &:last-child {
                border-bottom:      none;
            }
            &:hover, &.selected {
                background:         lightgrey;
            }
        }
    }

    &.open {
        ul.options {
            display: flex;
        }
        div.selected {
            border-bottom: none;
        }
    }
}
</style>