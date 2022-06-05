<template>
    <div 
        :class="$style.container"
    >
        <div :class="$style.targetCharacter">
            {{ targetCharacter }}
        </div>
        <div>
            <input 
                type="text" 
                @keydown="onKeyPressed" 
                :class="$style.input"
                autofocus
            />
        </div>
    </div>
</template>

<style lang="scss" module>
.container {
    padding: 3rem 1rem 0;
    display: flex;
    flex-direction: column;
    align-items: center;
}
.targetCharacter {
    font-size: 6rem;
}
.input {
    font-size: 2rem;
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
            const characters = `1234567890[]{}!@#$%^&*(){}?+_-.,;=/:\`~\\|`;
            const charactersExceptCurrent = characters.replace(this.targetCharacter, '');
            const randomIndex = Math.floor(Math.random() * charactersExceptCurrent.length);
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