<template>
    <div>
        <label for="toggle_button">
            <span v-if="isChecked" class="toggle__label label_on">On</span>
            <span v-if="! isChecked" class="toggle__label label_off">Off</span>

            <input type="checkbox" id="toggle_button" 
                    :disabled="disabled" 
                    v-model="isChecked"
                    @change="propagate"              
            />
            <span class="toggle__switch"></span>
        </label>
    </div>
</template>

<script>
export default {
    props: {
        disabled: {
            type: Boolean,
            default: false
        },
        modelValue: {
            type: Boolean,
        },
    },
    data(){
        return {
            isChecked: this.modelValue
        };
    },
    methods:{
        propagate(event){
            this.$emit("input", event.target.checked)
        }
    }
    
}
</script>

<style scoped>

#toggle_button{
    width: 0;
    height: 0;
    visibility: hidden;
    display:inline-block;
}
.toggle__switch{
    display:inline-block;
    width: 40px;
    height: 12px;
    background-color: #477a85;
    border-radius: 100px;
    position: relative;
    cursor: pointer;
    transition: 0.5s;
    box-shadow: 0 0 20px #477a8550;
}
.toggle__switch::after {
    content: "";
    width: 12px;
    height: 12px;
    background-color: #e8f5f7;
    position: absolute;
    border-radius: 70px;
    top: 0;
    left: -3px;
    transition: 0.5s;
}
#toggle_button:checked + .toggle__switch:after {
   left: calc(100% + 2px);
   transform: translateX(-100%);
}
#toggle_button:checked + .toggle__switch {
   background-color: #243d42;
}
.toggle__switch:active:after {
    width: 20px;
}
.label_off{
    color: red;
}
.label_on{
    color: green;
}

</style>