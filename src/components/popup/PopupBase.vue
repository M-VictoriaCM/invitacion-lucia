<script>
export default {
    name: 'BasePopup',
    props: {
        title: {
            type: String,
            required: true
        }
    },
    methods: {
        close() {
            this.$emit('close');
        }
    }
}
</script>

<template>
    <div class="pop-up">
        <div class="pop-up-inner">
            <div class="pop-up-close" @click="close">
                <i class="fa-solid fa-xmark icon__close"></i>
            </div>
            <div class="pop-up-body">
                <slot name="icon"></slot>
                <h1 class="title">{{ title }}</h1>
                <slot></slot>
            </div>
            <div class="pop-up-footer">
                <slot name="footer"></slot>
            </div>
        </div>
    </div>
</template>

<style scoped>
.pop-up{
    position:sticky;
    left:0;
    top:-10%;
    z-index:1000;
    height:100vh;
    width:100%;
    display:flex;
    flex-direction: column;
    justify-content: start;
    align-items: center;
}
.pop-up-inner{
    background-color: #fff;
    color:black;
    position:relative;
    padding:40px;
    border-radius:9px;
    width:320px;
    height:350px;
    box-shadow: 10px 10px 9px -9px rgba(0, 0, 0, 0.75);
    transition:all 250ms ease-in-out;
}
.fade-enter .pop-up-inner,
.fade-leave-to .pop-up-inner {
    opacity: 0;
    transform: translateY(-32px);
}
.fade-enter-active,
.fade-leave-active{
    transition:all 250ms ease-in-out
}
.fade-leave-active{
    transition-delay:250ms;
}
.icon__close{
    position:absolute;
    height:52px;
    width:52px;
    display:flex;
    border-radius:50%;
    padding:.5rem;
    margin:.5rem;
    justify-content: center;
    align-items: center;
    top:0;
    right:0;
    font-size:1.5rem;
    cursor:pointer;
    color:black;
}
.pop-up-body{
    width: 100%;
    height:90%;
    display:flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items:center ;
}
.title {
    font-family: "Playfair Display";
    font-style: italic;
    font-size: 1.5rem;
    font-weight: 500;
    color: #1E1E1E;
    text-align: center;
    margin:.5rem 0;
}
.pop-up-footer{
    width:100%;

    display: flex;
    justify-content:center;
}
@media(max-width:320px) {
    .pop-up-body{
        height:450px;
    }
}

@media(max-width:360px) {
    .pop-up-inner{
        width: 100%;
        height:530px;
    }
    .pop-up-body{
        height:90%;
    }
    .title{
        margin:0;
    }
}

@media (min-width: 768px) and (max-width: 991px){
    .pop-up-inner{
        width: 70%;
    }
}

@media (min-width: 1025px) {
    .pop-up-inner{
        width: 50%;
    }
    .pop-up-body{
        width:100%;
    }
}
</style>