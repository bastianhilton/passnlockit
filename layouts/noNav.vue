<template>
    <div>
        <HeaderNav />
        <Nuxt />
        <FooterNav />
    </div>
</template>

<script>
import HeaderNav from '~/components/HeaderNav'
import FooterNav from '~/components/FooterNav'

export default {
    components: { HeaderNav, FooterNav }    
}
</script>