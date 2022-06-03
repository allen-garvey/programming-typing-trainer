<template>
    <div 
        :class="$style.container"
    >
        <div :class="$style.targetCharacter">
            {{ targetCharacter }}
        </div>
        <input type="text" @keydown="onKeyPressed" />
    </div>
</template>

<style lang="scss" module>
.container {

}
.targetCharacter {
    font-size: 3.157rem;
}
</style>

<script>
export default {
    components: {
    },
    created(){
        this.generateTargetCharacter();
    },
    data(){
        return {
            targetCharacter: '',
        };
    },
    computed: {
    },
    methods: {
        generateTargetCharacter(){
            const characters = `1234567890[]{}!@#$%^&*(){}?+_-.;\`~\\|`;
            const charactersExceptCurrent = characters.replace(this.targetCharacter, '');
            const randomIndex = Math.floor(Math.random() * charactersExceptCurrent.length);
            console.log(randomIndex);
            console.log(charactersExceptCurrent);
            this.targetCharacter = charactersExceptCurrent[randomIndex];
        },
        onKeyPressed($event){
            if($event.key === this.targetCharacter){
                this.generateTargetCharacter();
            }
        },
    }
};
</script>