<template>
  <div class="dashboard-container">
    <aside class="sidebar">
      <div class="logo">Staff Portal</div>
      <nav class="nav-menu">
        <a href="#" class="active">Overview</a>
        <a href="#">Manage Users</a>
        <a href="#">Security Audit</a>
        <a href="#">Settings</a>
      </nav>
      <button @click="handleLogout" class="btn-logout">Logout</button>
    </aside>

    <main class="main-content">
      <header class="header">
        <h1>Welcome Back, Administrator</h1>
        <div class="user-badge">Role: Admin</div>
      </header>

      <section class="dashboard-grid">
        <div class="card">
          <h3>Tighter Security Mode</h3>
          <p>Multi-factor authentication required for all non-admin staff roles.</p>
        </div>
        <div class="card">
          <h3>Active Logins</h3>
          <p class="stat">1 Current Staff Session</p>
        </div>
        <div class="card">
          <h3>User Management</h3>
          <button class="action-btn">Add New Receptionist</button>
        </div>
      </section>
    </main>
  </div>
</template>

<script setup>
const handleLogout = () => {
  navigateTo('/admin/login')
}

useHead({
  title: 'Admin Dashboard',
  meta: [
    { name: 'description', content: 'Secure staff portal dashboard.' }
  ]
})
</script>

<style scoped>
.dashboard-container {
  display: flex;
  min-height: 100vh;
  background-color: #f9fafb;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

.sidebar {
  width: 240px;
  background-color: #1f2937;
  color: white;
  display: flex;
  flex-direction: column;
  padding: 1.5rem;
  box-sizing: border-box;
}

.logo {
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 2rem;
  color: #38bdf8;
}

.nav-menu {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  flex-grow: 1;
}

.nav-menu a {
  color: #9ca3af;
  text-decoration: none;
  padding: 0.75rem;
  border-radius: 6px;
  font-weight: 500;
  transition: all 0.15s ease-in-out;
}

.nav-menu a:hover, .nav-menu a.active {
  background-color: #374151;
  color: white;
}

.btn-logout {
  width: 100%;
  padding: 0.75rem;
  background-color: #dc2626;
  color: white;
  border: none;
  border-radius: 6px;
  font-weight: 600;
  cursor: pointer;
  margin-top: auto;
}

.main-content {
  flex-grow: 1;
  padding: 2.5rem;
  box-sizing: border-box;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 1px solid #e5e7eb;
  padding-bottom: 1.5rem;
  margin-bottom: 2rem;
}

h1 {
  font-size: 1.75rem;
  margin: 0;
  color: #111827;
}

.user-badge {
  background-color: #e0f2fe;
  color: #0369a1;
  padding: 0.25rem 0.75rem;
  border-radius: 9999px;
  font-size: 0.875rem;
  font-weight: 600;
}

.dashboard-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
}

.card {
  background: white;
  padding: 1.5rem;
  border-radius: 10px;
  box-shadow: 0 1px 3px rgba(0,0,0,0.1);
  border: 1px solid #e5e7eb;
}

.card h3 {
  margin: 0 0 1rem 0;
  color: #374151;
}

.stat {
  font-size: 1.5rem;
  font-weight: 700;
  color: #2563eb;
  margin: 0;
}

.action-btn {
  background-color: #059669;
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 6px;
  font-weight: 600;
  cursor: pointer;
}
</style>
