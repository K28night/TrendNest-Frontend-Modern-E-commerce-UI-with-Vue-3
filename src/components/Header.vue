<script setup>
import { ref, Teleport } from 'vue'

const open = ref(false)
const toggleForm = (formType) => {
    activeForm.value = formType
}
const activeForm = ref('login')
</script>

<template>

    <header class="site-header">
        <div class="container">
            <h1 class="logo">TrendNest</h1>

            <nav class="main-nav">
                <a href="#">Home</a>
                <a href="#">Shop</a>
                <a href="#">About</a>
                <a href="#">Contact</a>
            </nav>

            <form class="search-bar" @submit.prevent>
                <input type="text" placeholder="Search products..." />
                <button type="submit"> <span class="material-symbols-outlined">search</span></button>
            </form>

            <button class="lrbtn" @click="open = true">Login / Register</button>
        </div>
    </header>

    <Teleport to="body">
        <div v-if="open" class="modal-overlay" @click.self="open = false">
            <div class="modal">
                <div class="modal-header">
                    <button class="close-btn" @click="open = false">×</button>
                </div>

                <div class="tab-buttons">
                    <button :class="['tab', activeForm === 'login' ? 'active' : '']" @click="toggleForm('login')">
                        Login
                    </button>
                    <button :class="['tab', activeForm === 'register' ? 'active' : '']" @click="toggleForm('register')">
                        Register
                    </button>
                </div>

                <div class="form-section">
                    <div v-if="activeForm === 'login'" class="form">
                        <h2>Login</h2>
                        <input type="text" placeholder="Username" />
                        <input type="password" placeholder="Password" />
                        <button type="submit">Login</button>
                    </div>

                    <div v-else class="form">
                        <h2>Register</h2>
                        <input type="text" placeholder="Full Name" />
                        <input type="email" placeholder="Email" />
                        <input type="password" placeholder="Password" />
                        <input type="password" placeholder="Confirm Password" />
                        <input type="tel" name="phone" id="" placeholder="Phone Number">
                        <button type="submit">Register</button>
                    </div>
                </div>
            </div>
        </div>
    </Teleport>

</template>

<style scoped>
.site-header {
    width: 100%;
    background-color: #222831;
    color: #EEEEEE;
    padding: 1rem 0;
    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.2);
    position: fixed;
    /* Optional: stick to top */
    z-index: 100;
    top: 0;
    left: 0;

}

.container {
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 1rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.6);
    /* dark semi-transparent */
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 999;
    backdrop-filter: blur(2px);
    /* optional blur effect */
}

.logo {
    font-size: 1.6rem;
    font-family: "Space Grotesk", sans-serif;
    font-optical-sizing: auto;
    letter-spacing: 8px;
    font-style: normal;
    font-weight: bold;
}

.main-nav {
    display: flex;
    gap: 1.5rem;
}

.search-bar {
    display: flex;
    align-items: center;
    background-color: #EEEEEE;
    border-radius: 999px;
    padding: 0rem 0rem;
    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
}

.search-bar input {
    border: none;
    background: transparent;
    /* padding: 0.5rem 0.75rem; */
    flex: 1;
    font-size: 0.9rem;
    outline: none;
    color: #222831;
}

.search-bar button {
    background: none;
    border: none;
    cursor: pointer;
    color: #393E46;
    font-size: 1.4rem;
    padding: 0.3rem;
    border-radius: 25px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.search-bar button:hover {
    background-color: #00acb5c7;
}

.main-nav a {
    color: #EEEEEE;
    letter-spacing: 2px;
    text-decoration: none;
    transition: color 0.3s ease;
}

.main-nav a:hover {
    color: #00ADB5;
}

.lrbtn {
    background: #00ADB5;
    color: #EEEEEE;
    padding: 0.6rem 1.2rem;
    border: none;
    border-radius: 6px;
    cursor: pointer;
    font-weight: 500;
}

.modal {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: #222831;
    color: #EEEEEE;
    width: 90%;
    max-width: 400px;
    padding: 1.5rem;
    border-radius: 12px;
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.4);
    z-index: 1000;
}

.modal-header {
    display: flex;
    justify-content: flex-end;
}

.close-btn {
    background: transparent;
    color: #EEEEEE;
    font-size: 1.5rem;
    border: none;
    outline:none;
        position: relative;
    top: -25px;
    right: -1.5rem;
    cursor: pointer;

}

.tab-buttons {
    display: flex;
    justify-content: center;
    gap: 1rem;
    margin-top: -3rem;
}

.tab {
    flex: 1;
    max-width: 120px;
    padding: 0.6rem 1rem;
    border: 2px solid transparent;
    background-color: #393E46;
    color: #EEEEEE;
    border-radius: 30px;
    font-size: 0.95rem;
    font-weight: 500;
    outline: none;
    transition: all 0.3s ease;
    cursor: pointer;
    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.15);
}

.tab:hover {
    background-color: #00ADB5;
    color: #EEEEEE;
    transform: scale(1.05);
}

.tab.active {
    background-color: #00ADB5;
    color: #EEEEEE;
    border-color: #00ADB5;
    box-shadow: 0 4px 12px rgba(0, 173, 181, 0.4);
    transform: scale(1.05);
}



.form-section {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.form {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.form h2 {
    margin-bottom: 1rem;
}

input {
    width: 100%;
    max-width: 250px;
    margin-bottom: 1rem;
    padding: 0.5rem;
    border: 1px solid #00ADB5;
    border-radius: 4px;
    outline: none;
    background: #EEEEEE;
    color: #222831;
}

button[type="submit"] {
    background-color: #00ADB5;
    color: #EEEEEE;
    border: none;
    padding: 0.5rem 0.5rem;
    margin-right: 0.3rem;
    border-radius: 28px;
    cursor: pointer;
}
.btn-2 {
  color: #fff;
  cursor: pointer;
  font-size: 16px;
  font-weight: 400;
  line-height: 45px;
  max-width: 160px;
  width: 100%;
  text-transform: uppercase;
  background: transparent;
  border: none;
  position: relative;
  margin: 1rem auto;
  display: block;
  text-align: center;
  letter-spacing: 0;
  transition: all 0.3s ease;
}

.btn-2:hover,
.btn-2:active {
  letter-spacing: 5px;
}

.btn-2::before,
.btn-2::after {
  content: "";
  position: relative;
  display: block;
  width: 0;
  border: 1px solid transparent;
  transition: all 280ms ease-in-out;
  margin: 0 auto;
}

.btn-2:hover::before,
.btn-2:hover::after {
  border-color: #fff;
  width: 70%;
}

.btn-2::before {
  top: 0;
}

.btn-2::after {
  bottom: 0;
}

</style>
