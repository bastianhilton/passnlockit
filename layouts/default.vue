<template>
    <div>
        <HeaderNav />
        <main class="mb-5" style="margin-top: -55px;">
          <Nuxt />  
        </main>
        <categories />
        <FooterNav />
    </div>
</template>

<script>
import HeaderNav from '~/components/HeaderNav'
import FooterNav from '~/components/FooterNav'
import categories from '~/components/Passwords/categories'

export default {
    components: { HeaderNav, FooterNav, categories }    
}
</script>