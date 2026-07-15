
<script>
</script>
<div class="app-container">
  <nav class="sidebar">
    <div class="brand">SvelteDemo✨</div>
    <a href="/">🏠 Home</a>
    <a href="/about">✨ About</a>
    <a href="/dashboard">✨ Dashboard</a>
    <a href="/products">✨ Products</a>
    <a href="/settings">✨ Settings</a>
    <a href="/profile">✨ Profile</a>
    <a href="/analytics">✨ Analytics</a>
    <a href="/contact">✨ Contact</a>
  </nav>
  <main class="content">
    <slot />
  </main>
</div>
<style>
  :global(body) { margin: 0; font-family: 'Inter', sans-serif; background: #0f172a; color: #f8fafc; }
  .app-container { display: flex; min-height: 100vh; }
  .sidebar { width: 250px; background: #1e293b; padding: 2rem 1rem; display: flex; flex-direction: column; gap: 0.5rem; border-right: 1px solid #334155; }
  .brand { font-size: 1.5rem; font-weight: bold; margin-bottom: 2rem; color: #38bdf8; text-align: center; }
  .sidebar a { color: #cbd5e1; text-decoration: none; padding: 0.75rem 1rem; border-radius: 0.5rem; transition: all 0.3s ease; }
  .sidebar a:hover { background: #334155; color: #fff; transform: translateX(5px); }
  .content { flex: 1; padding: 3rem; overflow-y: auto; }
</style>
