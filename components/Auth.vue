<script setup>
const supabase = useSupabaseClient()

const loading = ref(false)
const email = ref('')

const handleLogin = async () => {
  try {
    loading.value = true
    const { error } = await supabase.auth.signInWithOtp({ email: email.value })
    if (error) throw error
    alert('Check your email for the login link!')
  } catch (error) {
    alert(error.error_description || error.message)
  } finally {
    loading.value = false
  }
}
</script>

<template>
    <div class="main">

        <div class="text-side">
            <h1 class="main-title"> 
             THE WAIT IS OVER. <br> THE WAITING LIST BEGINS. 
             </h1>
            <p class="description">
                Finding the perfect daycare is tough. <br>
                Finding a spot is tougher. <br>
                Tiny lists by Waitly makes it easy and transparent. <br><br>

                Sign up today and start planning for tomorrow.
             </p>
        </div>

        <div class="form-side">

                    <form @submit.prevent="handleLogin" class="form">

                        <div>
                            <input class="inputField" type="email" placeholder="Your email" v-model="email" />
                        </div>
                
                        <div>
                            <input
                            type="submit"
                            class="button block"
                            :value="loading ? 'Loading' : 'Sign up'"
                            :disabled="loading"
                            />
                        </div>
                    
                    
                    </form>

        </div>
    
    </div>
  
</template>

<style scoped>

*{
    box-sizing: border-box;
    margin: 0;
}
.main{
    width: 100vw;
    height: 100vh;
    box-sizing: border-box;
    margin: 0;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-around;
    overflow: hidden;
}

.form-side{
    border: 1px solid black;
    width: 50%;
    height: 80%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-around;
}

.form{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 80%;
    height: 50%;
    border: 1px solid black;
}

.form > div {
    margin: 1rem auto;
}

</style>

