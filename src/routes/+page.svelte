
<script>
  let time = new Date().toLocaleTimeString();
  let id = Math.random().toString(36).substr(2, 9);
  const stats = [
    { value: '8', label: 'Active Users' },
    { value: '99.9%', label: 'Uptime' },
    { value: '5.0★', label: 'Rating' },
    { value: '$18K', label: 'Revenue' }
  ];
</script>

<div class="page-header">
  <h1>Home <span class="badge">v1.1.0</span></h1>
  <p class="subtitle">Experience the power of SvelteKit with our blazing-fast, reactive interface.</p>
</div>

<div class="stat-row">
  {#each stats as s}
    <div class="stat-card">
      <span class="stat-value">{s.value}</span>
      <span class="stat-label">{s.label}</span>
    </div>
  {/each}
</div>

<div class="card-container">
  <div class="card"><h3>Welcome</h3><p>This is the central hub. Discover your potential.</p><button class="btn">Get Started</button></div>
  <div class="card"><h3>Quick Actions</h3><p>Access your most used tools instantly.</p><button class="btn">View Tools</button></div>
  <div class="card"><h3>Insights</h3><p>Gain clarity with real-time data and analytics.</p><button class="btn">View Insights</button></div>
</div>

<div class="dynamic-footer">
  <small>System ID: {id} | Last Sync: {time}</small>
</div>

<style>
  .page-header { margin-bottom: 2rem; }
  h1 { font-size: 3rem; margin: 0; background: linear-gradient(to right, #38bdf8, #818cf8); -webkit-background-clip: text; -webkit-text-fill-color: transparent; display: inline-flex; align-items: center; gap: 0.75rem; }
  .badge { font-size: 0.875rem; background: #818cf8; color: #fff; padding: 0.25rem 0.6rem; border-radius: 0.375rem; font-weight: 600; -webkit-text-fill-color: #fff; }
  .subtitle { color: #94a3b8; font-size: 1.2rem; margin-top: 0.5rem; }

  .stat-row { display: flex; gap: 1rem; flex-wrap: wrap; margin-bottom: 2.5rem; }
  .stat-card { background: #1e293b; border: 1px solid #334155; border-radius: 0.75rem; padding: 1.25rem 1.75rem; display: flex; flex-direction: column; gap: 0.25rem; flex: 1; min-width: 110px; }
  .stat-value { font-size: 1.85rem; font-weight: 700; color: #38bdf8; }
  .stat-label { font-size: 0.8rem; color: #64748b; text-transform: uppercase; letter-spacing: 0.05em; }

  .card-container { display: grid; gap: 2rem; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); margin-bottom: 3rem; }
  .card { background: #1e293b; border-radius: 1rem; padding: 2rem; border: 1px solid #334155; box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1); transition: transform 0.3s; }
  .card:hover { transform: translateY(-5px); border-color: #38bdf8; }
  .card h3 { color: #e2e8f0; margin-top: 0; }
  .card p { color: #94a3b8; line-height: 1.6; }
  .dynamic-footer { text-align: center; color: #64748b; margin-top: auto; padding-top: 2rem; border-top: 1px solid #334155; }
  .btn { display: inline-block; padding: 0.75rem 1.5rem; background: #38bdf8; color: #0f172a; font-weight: bold; border-radius: 0.5rem; text-decoration: none; margin-top: 1rem; cursor: pointer; border: none; }
  .btn:hover { background: #7dd3fc; }
</style>
