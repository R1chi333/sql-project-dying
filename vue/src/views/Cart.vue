<script>
import { useAuthStore } from '../stores/ah';
import { storeToRefs } from 'pinia';

export default {
  setup() {
    const authStore = useAuthStore()
    const { currentUser } = storeToRefs(authStore)
    return {
      currentUser,
    }
  },
}
</script>
<template>
    <div>
        <h1>{{ currentUser }}</h1>
    </div>
</template>