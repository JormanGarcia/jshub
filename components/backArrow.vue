<template>
    <svg @click="setActive" :class="{animate: isActive}" version="1.1" id="svg" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
	 width="459px" height="459px" viewBox="0 0 459 459" fill="#aaa" xml:space="preserve">
<g>
	<g id="reply">
		<path d="M178.5,140.25v-102L0,216.75l178.5,178.5V290.7c127.5,0,216.75,40.8,280.5,130.05C433.5,293.25,357,165.75,178.5,140.25z"
			/>
	</g>
</g>
<g>
</g>
<g>
</g>
<g>
</g>
<g>
</g>
<g>
</g>
<g>
</g>
<g>
</g>
<g>
</g>
<g>
</g>
<g>
</g>
<g>
</g>
<g>
</g>
<g>
</g>
<g>
</g>
<g>
</g>
</svg>
</template>

<script>
export default {
    data: function() {
        return {
            isActive: false
        }
    }, methods: {
        setActive: function(){
            this.isActive = true;
            this.$emit('toggle')
        }
    }
}
</script>

<style>
#svg {
     width: 45px;
     height: 45px;
    border: 1px solid black;
    border-radius: 50%;
    padding: 10px;
    fill: black;
    opacity: .2;
    transition: .1s;
    position: absolute;
    top: 15px;
    left: 20px;
    cursor: pointer;
    z-index: 20;
}

#svg:hover {

    opacity: 1;
}

#svg.animate {
    animation: click .5s;

}



@keyframes click {
    
    0%{
        transform: rotate(0);
        background: var(--main-color);

    }

    25% {
        transform: rotate(25deg);
        background: var(--main-color);
    }

    75% {
        transform: rotate(-25deg);
    }

    100% {
        transform: rotate(0);

    }
    
}


</style>