<script>
  import { onMount } from 'svelte';

  let time = new Date().toLocaleTimeString();
  let id = Math.random().toString(36).substr(2, 9);
  const stats = [
    { value: '8', label: 'Active Users' },
    { value: '99.9%', label: 'Uptime' },
    { value: '5.0', label: 'Rating' },
    { value: '$18K', label: 'Revenue' }
  ];

  // TCSE/ADE Certification — Advertisement state
  let cookieVisible = true;
  let chatOpen = false;
  let promoVisible = true;
  let newsletterVisible = false;
  let dynamicAdLoaded = false;

  onMount(() => {
    // Delayed newsletter popup (simulates marketing tool)
    const t1 = setTimeout(() => { newsletterVisible = true; }, 3500);
    // Lazy-loaded dynamic ad (simulates ad network injection)
    const t2 = setTimeout(() => { dynamicAdLoaded = true; }, 2000);
    return () => { clearTimeout(t1); clearTimeout(t2); };
  });
</script>

<!-- TCSE: Leaderboard Banner Ad (IAB 728x90) - CSS: .ad-banner -->
<div class="ad-banner" aria-label="Advertisement" role="complementary">
  <span class="ad-text">SvelteKit Pro — Build Faster, Deploy Anywhere. Save 35% Today.</span>
  <span class="ad-label">Sponsored</span>
  <button class="ad-btn">Get Offer</button>
</div>

<!-- TCSE: Sponsored Announcement Banner - CSS: .affiliate-banner, .banner-ad -->
<div class="affiliate-banner banner-ad" aria-label="Affiliate advertisement">
  <div class="affiliate-content">
    <div class="affiliate-brand">Affiliate Partner</div>
    <div class="affiliate-title">Netlify — Host Your SvelteKit App Free</div>
    <div class="affiliate-desc">Save 20% on Pro plan with our exclusive link</div>
  </div>
  <button class="affiliate-btn">Claim Deal</button>
</div>

<div class="page-header">
  <h1>Home <span class="badge">v1.2.0 TCSE Certified</span></h1>
  <p class="subtitle">SvelteKit + UVT — TCSE/ADE Advertisement Detection Certification</p>
</div>

<!-- TCSE: Sponsored Cards Section - CSS: .sponsored-card, .sponsored-content -->
<div class="sponsored-section">
  <div class="sponsored-label">Sponsored Content</div>
  <div class="sponsored-grid">
    <div class="sponsored-card sponsored-content" aria-label="Sponsored content">
      <div class="sponsor-tag">Sponsor · Supabase</div>
      <div class="sponsor-title">Open Source Firebase Alternative</div>
      <div class="sponsor-desc">PostgreSQL database with instant APIs, realtime subscriptions, and auth.</div>
      <button class="sponsor-btn">Start Free</button>
    </div>
    <div class="sponsored-card sponsored-content" aria-label="Sponsored content">
      <div class="sponsor-tag">Sponsor · PlanetScale</div>
      <div class="sponsor-title">MySQL-Compatible Serverless DB</div>
      <div class="sponsor-desc">Branches, non-blocking schema changes, and unlimited connections.</div>
      <button class="sponsor-btn">Try Free</button>
    </div>
  </div>
</div>

<div class="stat-row">
  {#each stats as s}
    <div class="stat-card">
      <span class="stat-value">{s.value}</span>
      <span class="stat-label">{s.label}</span>
    </div>
  {/each}
</div>

<!-- TCSE: Dynamic lazy-loaded ad - .ad-unit, data-ad-inserted="true" -->
<div class="dynamic-ad-slot">
  {#if dynamicAdLoaded}
    <div class="ad-unit dynamic-ad" data-ad-inserted="true" aria-label="Advertisement">
      <span class="dynamic-ad-icon">⭐</span>
      <div>
        <div class="dynamic-ad-title">Upgrade to Svelte Premium</div>
        <div class="dynamic-ad-sub">Dynamically loaded — simulates ad network lazy injection</div>
      </div>
    </div>
  {:else}
    <div class="ad-unit ad-loading">Loading sponsored content...</div>
  {/if}
</div>

<div class="card-container">
  <div class="card"><h3>Welcome</h3><p>Central hub. Discover your potential.</p><button class="btn">Get Started</button></div>
  <div class="card"><h3>Quick Actions</h3><p>Access your most used tools instantly.</p><button class="btn">View Tools</button></div>
  <div class="card"><h3>Insights</h3><p>Real-time data and analytics.</p><button class="btn">View Insights</button></div>
</div>

<div class="dynamic-footer">
  <small>System ID: {id} | Last Sync: {time}</small>
</div>

<!-- TCSE: Cookie Consent Banner - #cookie-consent, .cookie-banner -->
{#if cookieVisible}
  <div id="cookie-consent" class="cookie-banner">
    <p class="cookie-text">We use cookies for analytics and to serve personalized advertisements. <strong>Cookie Policy</strong></p>
    <div class="cookie-btns">
      <button class="cookie-accept" on:click={() => cookieVisible = false}>Accept All</button>
      <button class="cookie-decline" on:click={() => cookieVisible = false}>Decline</button>
    </div>
  </div>
{/if}

<!-- TCSE: Chat Widget - .chat-widget, #chat-button -->
<div class="chat-widget">
  {#if chatOpen}
    <div class="chat-panel">
      <div class="chat-header">Svelte Support</div>
      <div class="chat-body">Hi! How can we help with your SvelteKit project today?</div>
      <input class="chat-input" placeholder="Type your message..." />
    </div>
  {/if}
  <button id="chat-button" class="chat-btn" on:click={() => chatOpen = !chatOpen}>Chat</button>
</div>

<!-- TCSE: Floating Promotion - .floating-ad, .sticky-ad -->
{#if promoVisible}
  <div class="floating-ad sticky-ad" aria-label="Promotional offer">
    <button class="promo-close" on:click={() => promoVisible = false}>x</button>
    <div class="promo-title">Svelte Pro Bundle</div>
    <div class="promo-sub">Save 40% — Limited Time</div>
    <button class="promo-cta">Get Offer</button>
  </div>
{/if}

<!-- TCSE: Newsletter Popup - .newsletter-popup -->
{#if newsletterVisible}
  <div class="newsletter-popup" role="dialog">
    <button class="newsletter-close" on:click={() => newsletterVisible = false}>x</button>
    <h3 class="newsletter-title">Svelte Weekly Tips</h3>
    <p class="newsletter-desc">Get weekly SvelteKit tutorials and exclusive deals.</p>
    <input class="newsletter-email" placeholder="your@email.com" />
    <button class="newsletter-submit">Subscribe</button>
  </div>
{/if}

<style>
  /* TCSE: Leaderboard Ad */
  .ad-banner {
    max-width: 728px; height: 90px; margin: 0 auto 16px;
    background: linear-gradient(135deg, #f0fdf4, #dcfce7);
    border: 1px solid #86efac; border-radius: 8px;
    display: flex; align-items: center; justify-content: space-between;
    padding: 0 20px; gap: 12px; box-sizing: border-box;
  }
  .ad-text { font-weight: 700; color: #166534; font-size: 13px; flex: 1; }
  .ad-label { background: #064e3b; color: #4ade80; font-size: 10px; padding: 3px 8px; border-radius: 12px; white-space: nowrap; }
  .ad-btn { padding: 8px 14px; background: #16a34a; color: #fff; border: none; border-radius: 6px; font-weight: 600; cursor: pointer; font-size: 12px; white-space: nowrap; }

  /* TCSE: Affiliate Banner */
  .affiliate-banner {
    background: linear-gradient(135deg, #0f172a, #1e3a5f); color: #fff;
    border-radius: 10px; padding: 14px 20px; display: flex;
    align-items: center; justify-content: space-between; gap: 16px;
    margin-bottom: 16px; box-shadow: 0 4px 16px rgba(15,23,42,0.4);
  }
  .affiliate-brand { font-size: 9px; color: #60a5fa; text-transform: uppercase; letter-spacing: 1px; margin-bottom: 3px; }
  .affiliate-title { font-weight: 700; font-size: 14px; }
  .affiliate-desc { font-size: 11px; color: #94a3b8; }
  .affiliate-btn { padding: 9px 18px; background: #2563eb; color: #fff; border: none; border-radius: 8px; font-weight: 600; cursor: pointer; white-space: nowrap; font-size: 12px; }

  /* Sponsored section */
  .sponsored-section { margin-bottom: 20px; }
  .sponsored-label { font-size: 10px; color: #64748b; text-transform: uppercase; letter-spacing: 1px; margin-bottom: 8px; }
  .sponsored-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 12px; }
  .sponsored-card { border: 1px solid #334155; border-radius: 10px; padding: 14px; background: #1e293b; display: flex; flex-direction: column; gap: 6px; }
  .sponsor-tag { font-size: 9px; color: #64748b; text-transform: uppercase; letter-spacing: 1px; }
  .sponsor-title { font-weight: 700; color: #f8fafc; font-size: 14px; }
  .sponsor-desc { font-size: 12px; color: #94a3b8; line-height: 1.4; }
  .sponsor-btn { padding: 7px 12px; background: #38bdf8; color: #0f172a; border: none; border-radius: 6px; font-weight: 600; cursor: pointer; font-size: 12px; align-self: flex-start; }

  /* Dynamic ad */
  .dynamic-ad-slot { margin-bottom: 16px; }
  .ad-unit { border-radius: 8px; padding: 12px 16px; }
  .dynamic-ad { background: linear-gradient(135deg, #fefce8, #fef9c3); border: 1px solid #fde68a; display: flex; align-items: center; gap: 12px; }
  .dynamic-ad-icon { font-size: 24px; }
  .dynamic-ad-title { font-weight: 700; font-size: 13px; color: #92400e; }
  .dynamic-ad-sub { font-size: 11px; color: #78350f; }
  .ad-loading { background: #1e293b; border: 1px solid #334155; color: #64748b; font-size: 12px; text-align: center; }

  /* Cookie Banner */
  .cookie-banner {
    position: fixed; bottom: 0; left: 0; right: 0;
    background: #1f2937; color: #f9fafb; padding: 14px 24px;
    display: flex; align-items: center; justify-content: space-between;
    z-index: 9999; gap: 16px; flex-wrap: wrap;
  }
  .cookie-text { margin: 0; font-size: 13px; }
  .cookie-btns { display: flex; gap: 8px; }
  .cookie-accept { padding: 7px 14px; background: #10b981; color: #fff; border: none; border-radius: 6px; cursor: pointer; font-weight: 600; font-size: 12px; }
  .cookie-decline { padding: 7px 14px; background: transparent; color: #9ca3af; border: 1px solid #4b5563; border-radius: 6px; cursor: pointer; font-size: 12px; }

  /* Chat Widget */
  .chat-widget { position: fixed; bottom: 80px; right: 20px; z-index: 9998; }
  .chat-panel { width: 250px; height: 270px; background: #1e293b; border-radius: 12px; box-shadow: 0 8px 32px rgba(0,0,0,0.3); padding: 14px; margin-bottom: 8px; display: flex; flex-direction: column; gap: 8px; border: 1px solid #334155; }
  .chat-header { font-weight: 700; font-size: 13px; color: #38bdf8; }
  .chat-body { flex: 1; background: #0f172a; border-radius: 8px; padding: 8px; font-size: 12px; color: #94a3b8; }
  .chat-input { padding: 6px; background: #0f172a; border: 1px solid #334155; border-radius: 6px; font-size: 12px; color: #f8fafc; }
  .chat-btn { width: 48px; height: 48px; border-radius: 50%; background: #38bdf8; color: #0f172a; border: none; font-size: 13px; cursor: pointer; display: block; margin-left: auto; box-shadow: 0 4px 12px rgba(56,189,248,0.4); font-weight: 700; }

  /* Floating Ad */
  .floating-ad { position: fixed; bottom: 140px; right: 20px; z-index: 9997; background: linear-gradient(135deg, #0ea5e9, #0284c7); color: #fff; border-radius: 12px; padding: 12px 16px; width: 185px; box-shadow: 0 8px 24px rgba(14,165,233,0.4); }
  .promo-close { position: absolute; top: 6px; right: 8px; background: none; border: none; color: rgba(255,255,255,0.6); font-size: 13px; cursor: pointer; }
  .promo-title { font-weight: 800; font-size: 13px; margin-bottom: 3px; }
  .promo-sub { font-size: 11px; opacity: 0.9; margin-bottom: 8px; }
  .promo-cta { width: 100%; padding: 6px; background: #fff; color: #0ea5e9; border: none; border-radius: 6px; font-weight: 700; font-size: 11px; cursor: pointer; }

  /* Newsletter Popup */
  .newsletter-popup { position: fixed; top: 50%; left: 50%; transform: translate(-50%,-50%); background: #1e293b; border: 1px solid #334155; border-radius: 16px; padding: 28px; width: 340px; box-shadow: 0 20px 60px rgba(0,0,0,0.4); z-index: 10000; color: #f8fafc; }
  .newsletter-close { position: absolute; top: 10px; right: 12px; background: none; border: none; font-size: 18px; cursor: pointer; color: #64748b; }
  .newsletter-title { margin: 0 0 8px; font-size: 20px; font-weight: 800; }
  .newsletter-desc { margin: 0 0 14px; color: #94a3b8; font-size: 13px; }
  .newsletter-email { width: 100%; padding: 9px 12px; background: #0f172a; border: 1px solid #334155; border-radius: 7px; font-size: 13px; margin-bottom: 10px; box-sizing: border-box; color: #f8fafc; }
  .newsletter-submit { width: 100%; padding: 10px; background: #38bdf8; color: #0f172a; border: none; border-radius: 8px; font-weight: 700; cursor: pointer; font-size: 14px; }

  /* Page styles */
  .page-header { margin-bottom: 1.5rem; }
  h1 { font-size: 2.5rem; margin: 0; background: linear-gradient(to right, #38bdf8, #818cf8); -webkit-background-clip: text; -webkit-text-fill-color: transparent; display: inline-flex; align-items: center; gap: 0.75rem; }
  .badge { font-size: 0.75rem; background: #818cf8; color: #fff; padding: 0.25rem 0.6rem; border-radius: 0.375rem; font-weight: 600; -webkit-text-fill-color: #fff; }
  .subtitle { color: #94a3b8; font-size: 1rem; margin-top: 0.5rem; }
  .stat-row { display: flex; gap: 1rem; flex-wrap: wrap; margin-bottom: 1.5rem; }
  .stat-card { background: #1e293b; border: 1px solid #334155; border-radius: 0.75rem; padding: 1.25rem 1.75rem; display: flex; flex-direction: column; gap: 0.25rem; flex: 1; min-width: 110px; }
  .stat-value { font-size: 1.85rem; font-weight: 700; color: #38bdf8; }
  .stat-label { font-size: 0.8rem; color: #64748b; text-transform: uppercase; letter-spacing: 0.05em; }
  .card-container { display: grid; gap: 2rem; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); margin-bottom: 2rem; }
  .card { background: #1e293b; border-radius: 1rem; padding: 2rem; border: 1px solid #334155; transition: transform 0.3s; }
  .card:hover { transform: translateY(-5px); border-color: #38bdf8; }
  .card h3 { color: #e2e8f0; margin-top: 0; }
  .card p { color: #94a3b8; line-height: 1.6; }
  .dynamic-footer { text-align: center; color: #64748b; padding-top: 1.5rem; border-top: 1px solid #334155; }
  .btn { display: inline-block; padding: 0.75rem 1.5rem; background: #38bdf8; color: #0f172a; font-weight: bold; border-radius: 0.5rem; cursor: pointer; border: none; margin-top: 0.75rem; }
  .btn:hover { background: #7dd3fc; }
</style>