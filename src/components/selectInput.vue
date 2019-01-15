<template>
    <div class="selectInput" :class="{open: open}">
        <div class="selected"> <!-- Selected container -->
            <span>Selected</span>
            <label for="toggleSelect">
                <i>+</i><!-- icon -->
                <input type="checkbox" v-model="open" id="toggleSelect" name="toggleSelect" />
            </label>
        </div>
        <ul class="options"> <!-- Options -->
            <li>Option 1</li>
            <li>Option 2</li>
            <li>Option 3</li>
            <li>Option 4</li>        
        </ul>
    </div>
</template>

<script>
export default {
    name: 'selectInput',
    data() {
        return {
            open: false
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
        span {
            padding-left:   10px;
        }
        label {
            margin-left:    auto;
            cursor: pointer;
            i {
                font-style:     normal;
                color:          lightgrey;
            }
            input[type="checkbox"] {
                display: none;
            }
        }
    }
    ul.options {
        list-style-type:    none;
        padding: 0;
        width: 100%;
        flex-direction: column;
        text-align:         left;
        border:             1px solid lightgrey;
        margin: 0;
        display: none;
        li {
            padding: 5px 10px;
            border-bottom: 1px solid lightgrey;
            &:first-child {
                border-top: none;                
            }
            &:last-child {
                border-bottom: none;
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