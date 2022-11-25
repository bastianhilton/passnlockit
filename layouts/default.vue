<template>
    <div>
        <HeaderNav />
        <main class="mb-5" style="margin-top: -55px;">
          <Nuxt />  
        </main>
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