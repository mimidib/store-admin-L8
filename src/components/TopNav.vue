<template>
  <div class="nav-wrapper">
    <!-- Top bar: logo + admin label -->
    <nav class="top-bar">
      <div class="logo">
        <a href="/">
          <img src="/best-buy-logo.png" alt="Best Buy Logo">
        </a>
        <span class="admin-label">Admin Portal</span>
      </div>
      <button class="hamburger" @click="toggleNav">
        <span class="hamburger-icon"></span>
      </button>
    </nav>
    <!-- Nav link bar -->
    <div class="category-bar">
      <ul class="nav-links" :class="{ 'nav-links--open': isNavOpen }">
        <li>
          <router-link to="/orders" @click="closeNav">
            Orders
            <svg class="chevron" focusable="false" viewBox="0 0 32 32" aria-hidden="true">
              <path d="M16,20.5a1,1,0,0,1-.74-.29l-7-6.91a1,1,0,0,1,0-1.48,1.06,1.06,0,0,1,1.49,0L16,17.92l6.18-6.13a1.06,1.06,0,0,1,1.49,0,1,1,0,0,1,0,1.48l-7,6.91A1,1,0,0,1,16,20.5Z"/>
            </svg>
          </router-link>
        </li>
        <li>
          <router-link to="/products" @click="closeNav">
            Products
            <svg class="chevron" focusable="false" viewBox="0 0 32 32" aria-hidden="true">
              <path d="M16,20.5a1,1,0,0,1-.74-.29l-7-6.91a1,1,0,0,1,0-1.48,1.06,1.06,0,0,1,1.49,0L16,17.92l6.18-6.13a1.06,1.06,0,0,1,1.49,0,1,1,0,0,1,0,1.48l-7,6.91A1,1,0,0,1,16,20.5Z"/>
            </svg>
          </router-link>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TopNav',
  data() {
    return {
      isNavOpen: false
    }
  },
  methods: {
    toggleNav() {
      this.isNavOpen = !this.isNavOpen
    },
    closeNav() {
      this.isNavOpen = false
    }
  }
}
</script>

<style scoped>
.nav-wrapper {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
}

/* Top bar */
.top-bar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #0046BE;
  color: #fff;
  padding: 0.5rem 1rem 0.25rem 1rem;
}

.logo {
  display: flex;
  align-items: center;
  gap: 12px;
}

.top-bar img {
  width: 90px;
  height: auto;
}

.admin-label {
  font-size: 1.1rem;
  font-weight: 700;
  color: #fff;
  letter-spacing: 0.02em;
}

/* Nav link bar */
.category-bar {
  background-color: #003099;
  padding: 0;
}

.nav-links {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
  justify-content: center;
}

.nav-links li a {
  display: flex;
  align-items: center;
  gap: 6px;
  color: #fff;
  text-decoration: none;
  font-size: 0.95rem;
  font-weight: 700;
  font-family: 'Arial', sans-serif;
  letter-spacing: 0.01em;
  padding: 0.65rem 1.4rem;
  border-bottom: 3px solid transparent;
  white-space: nowrap;
  transition: border-color 0.15s, background-color 0.15s;
}

.nav-links li a:hover,
.nav-links li a.router-link-active {
  background-color: rgba(255, 255, 255, 0.1);
  border-bottom: 3px solid #FFE000;
}

.chevron {
  width: 18px;
  height: 18px;
  fill: #fff;
  flex-shrink: 0;
  position: relative;
  top: 1px;
}

.hamburger {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0;
}

.hamburger-icon {
  display: block;
  width: 20px;
  height: 2px;
  background-color: #fff;
  position: relative;
}

.hamburger-icon::before,
.hamburger-icon::after {
  content: '';
  display: block;
  width: 20px;
  height: 2px;
  background-color: #fff;
  position: absolute;
  left: 0;
}

.hamburger-icon::before { top: -6px; }
.hamburger-icon::after  { bottom: -6px; }

@media (max-width: 768px) {
  .nav-links {
    display: none;
    flex-direction: column;
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    background-color: #003099;
    padding: 0.5rem 0;
  }

  .nav-links--open {
    display: flex;
  }

  .hamburger {
    display: block;
  }
}
</style>