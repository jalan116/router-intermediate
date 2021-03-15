<template>
    <div class="navbar mb-2 shadow-lg bg-neutral text-neutral-content">
  <div class="flex-1 px-2 mx-2">
    <span class="text-lg font-bold">
            Login Example
          </span>
  </div> 
  <div class="flex-none hidden px-2 mx-2 lg:flex">
    <div class="flex items-stretch">
      <router-link to="/" class="btn btn-ghost btn-sm rounded-btn">
              Home
            
      </router-link> 
      
      <router-link v-if="!isAuthenticated" to="/login" class="btn btn-ghost btn-sm rounded-btn">
              Login
            
      </router-link>
      <div  v-else>
        <router-link  to="/secret" class="btn btn-ghost btn-sm rounded-btn">
              Secret Page
            
        </router-link>
        <button to="/login" class="btn btn-error btn-sm rounded-btn hover:text-content-100" @click="logout">
              Logout
            
        </button>
        
      </div>
    </div>
  </div> 
</div>
</template>

<script setup>
import { useRouter } from 'vue-router'
import { isAuthenticated, signOut } from '../helpers/useAuth.js'
const router = useRouter()
const logout = async () => {
  await signOut()
  router.push('/')
}
</script>
