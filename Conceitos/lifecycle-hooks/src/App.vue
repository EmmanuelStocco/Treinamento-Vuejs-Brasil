<template>
    <h1> Lifecycle Hooks</h1>
</template>

<script>
export default {
    setup () {
        onMounted(() => { //versão composition API
            console.log('Foi montado composition API')
        })
    }
}

    // export default {
    //     mounted() {
    //         console.log('Foi montado options APIO')
    //     }
    // }
</script>
