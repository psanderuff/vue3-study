<template>
  <custom-header
    @create-account="handleAccountCreate"
    @login="handleLogin"
  />
  <contact/>
  <div class="flex justify-center py-10 bg-brand-gray">
    <p class="font-medium text-center text-gray-800"> feedbacker © 2022</p>
  </div>
</template>
<script>
import { onMounted } from 'vue'
import CustomHeader from './components/CustomHeader'
import Contact from './components/Contact.vue'
import { useRouter } from 'vue-router'
import useModal from '@/hooks/useModal'

export default {
  components: { CustomHeader, Contact },
  setup () {
    const router = useRouter()
    const modal = useModal()

    onMounted(() => {
      const token = window.localStorage.getItem('token')
      if (token) {
        router.push({ name: 'FeedBacks' })
      }
    })

    function handleLogin () {
      modal.open({
        component: 'ModalLogin'
      })
    }

    function handleAccountCreate () {
      modal.open({
        component: 'ModalCreateAccount'
      })
    }

    return {
      handleLogin,
      handleAccountCreate
    }
  }
}
</script>
<style>

</style>
