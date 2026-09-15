<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Nexa Commerce API v1 — Developer Reference · Gopala Krishna Soma.</title>
<meta name="description" content="Developer reference documentation for the Nexa Commerce REST API v1 — a fictional B2B commerce platform.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#f5f5f2;
    --surface:#ffffff;
    --ink:#161a1f;
    --muted:#5a6169;
    --faint:#8a9098;
    --border:#dfe1de;
    --border-strong:#c7cac6;
    --accent:#b8541c;
    --accent-ink:#7c3a12;
    --code-bg:#12151a;
    --code-ink:#dde3ea;
    --code-border:#242a32;
    --get:#1a5fb4;
    --post:#1a7a4c;
    --patch:#a8790a;
    --delete:#b3372c;
    --radius:3px;
    --sidebar-w:288px;
  }
  *{box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    margin:0;
    background:var(--bg);
    color:var(--ink);
    font-family:'IBM Plex Sans', Arial, sans-serif;
    font-size:16px;
    line-height:1.6;
    -webkit-font-smoothing:antialiased;
  }
  code, pre, .mono{font-family:'IBM Plex Mono', Consolas, monospace;}

  a{color:var(--accent-ink); text-decoration:none;}
  a:hover{text-decoration:underline;}
  a:focus-visible, button:focus-visible, summary:focus-visible{outline:2px solid var(--accent); outline-offset:2px;}

  /* ---------- layout shell ---------- */
  .shell{display:flex; max-width:1280px; margin:0 auto;}

  /* ---------- sidebar ---------- */
  .sidebar{
    width:var(--sidebar-w);
    flex-shrink:0;
    border-right:1px solid var(--border);
    position:sticky;
    top:0;
    align-self:flex-start;
    height:100vh;
    overflow-y:auto;
    padding:0 0 32px;
    background:var(--bg);
  }
  .sidebar-head{
    padding:22px 22px 16px;
    border-bottom:1px solid var(--border);
    position:sticky;
    top:0;
    background:var(--bg);
    z-index:5;
  }
  .brand{display:flex; align-items:baseline; gap:8px; margin:0;}
  .brand-mark{
    width:9px; height:9px; border-radius:1px;
    background:var(--accent); flex-shrink:0; margin-bottom:1px;
    display:inline-block;
  }
  .brand-name{font-size:16px; font-weight:600; letter-spacing:-0.01em;}
  .brand-sub{margin:2px 0 12px; font-size:12.5px; color:var(--muted);}
  .base-url-chip{
    display:flex; align-items:center; gap:8px;
    background:var(--surface); border:1px solid var(--border-strong);
    border-radius:var(--radius); padding:8px 9px;
    font-size:12px;
  }
  .base-url-chip code{
    flex:1; overflow-x:auto; white-space:nowrap; color:var(--ink);
    font-size:11.5px;
  }
  .copy-btn{
    border:none; background:transparent; cursor:pointer;
    color:var(--muted); font-size:11px; font-family:inherit;
    padding:2px 4px; border-radius:2px; flex-shrink:0;
  }
  .copy-btn:hover{color:var(--ink); background:var(--bg);}

  nav.toc{padding:14px 12px 0;}
  .toc-group{margin-bottom:2px;}
  .toc-group-label{
    display:block; padding:10px 10px 4px;
    font-size:11px; color:var(--faint); font-weight:600;
    letter-spacing:0.03em;
  }
  .toc a{
    display:block; padding:6px 10px; border-radius:var(--radius);
    color:var(--muted); font-size:13.5px; text-decoration:none;
    border-left:2px solid transparent;
  }
  .toc a:hover{color:var(--ink); background:var(--surface);}
  .toc a.active{
    color:var(--accent-ink); border-left-color:var(--accent);
    background:var(--surface); font-weight:500;
  }
  .toc .endpoint-link{
    display:flex; gap:8px; align-items:baseline; padding-left:20px;
    font-size:12.5px;
  }
  .toc .m{
    font-family:'IBM Plex Mono', monospace; font-size:9.5px; font-weight:600;
    padding:1px 4px; border-radius:2px; flex-shrink:0; letter-spacing:0.02em;
  }
  .m-get{color:var(--get); background:color-mix(in srgb, var(--get) 12%, white);}
  .m-post{color:var(--post); background:color-mix(in srgb, var(--post) 12%, white);}
  .m-patch{color:var(--patch); background:color-mix(in srgb, var(--patch) 14%, white);}
  .m-delete{color:var(--delete); background:color-mix(in srgb, var(--delete) 12%, white);}

  .sidebar-toggle{display:none;}

  /* ---------- main content ---------- */
  main{flex:1; min-width:0; padding:0 0 80px;}
  .content-wrap{max-width:760px; margin:0 auto; padding:0 40px;}

  header.hero{
    padding:56px 40px 40px;
    border-bottom:1px solid var(--border);
    margin-bottom:8px;
  }
  header.hero .content-wrap{padding:0;}
  .hero-eyebrow{
    font-size:12.5px; color:var(--accent-ink); font-weight:500;
    margin:0 0 14px;
  }
  h1.hero-title{
    font-size:40px; margin:0 0 10px; letter-spacing:-0.015em;
    font-weight:600; line-height:1.15;
  }
  .hero-desc{
    font-size:16.5px; color:var(--muted); max-width:56ch; margin:0 0 26px;
  }
  .hero-byline{font-size:14px; color:var(--muted); margin:0 0 26px;}
  .hero-byline strong{color:var(--ink); font-weight:600;}
  .hero-purpose{
    margin-top:26px; padding:20px 22px; background:var(--surface);
    border:1px solid var(--border); border-left:2px solid var(--accent);
    border-radius:0 6px 6px 0; max-width:64ch;
  }
  .hero-purpose-title{font-size:13px; font-weight:600; margin:0 0 10px; color:var(--ink);}
  .hero-purpose p{font-size:14px; color:var(--muted); margin:0 0 10px;}
  .hero-purpose p:last-child{margin-bottom:0;}
  .hero-disclaimer{font-style:italic; color:var(--faint); font-size:13px;}
  .hero-stats{display:flex; gap:0; flex-wrap:wrap; border-top:1px solid var(--border); margin-top:22px;}
  .hero-stat{
    padding:16px 24px 4px 0; margin-right:24px; border-right:1px solid var(--border);
  }
  .hero-stat:last-child{border-right:none;}
  .hero-stat b{display:block; font-size:22px; font-weight:600;}
  .hero-stat span{font-size:12.5px; color:var(--muted);}

  section{padding:46px 40px; border-bottom:1px solid var(--border);}
  section:last-of-type{border-bottom:none;}
  .content-wrap > section{padding:46px 0;}

  .section-head{display:flex; align-items:baseline; gap:12px; margin-bottom:6px;}
  .section-num{
    font-family:'IBM Plex Mono', monospace; font-size:13px; color:var(--faint);
    flex-shrink:0;
  }
  h2{font-size:24px; margin:0; font-weight:600; letter-spacing:-0.01em;}
  section > p.section-intro{color:var(--muted); margin:10px 0 28px; max-width:64ch;}

  h3{font-size:18px; font-weight:600; margin:34px 0 10px;}
  h3:first-of-type{margin-top:8px;}
  h4{font-size:15px; font-weight:600; margin:0 0 4px;}
  h5{
    font-size:11px; text-transform:none; color:var(--faint);
    font-weight:600; margin:18px 0 8px; letter-spacing:0.02em;
  }
  p{margin:0 0 14px; max-width:68ch;}
  .note{
    border-left:2px solid var(--accent); background:var(--surface);
    padding:12px 16px; border-radius:0 var(--radius) var(--radius) 0;
    color:var(--muted); font-size:14.5px; margin:18px 0;
  }
  .note strong{color:var(--ink);}

  table{border-collapse:collapse; width:100%; margin:14px 0 24px; font-size:14px;}
  caption{text-align:left; font-size:12px; color:var(--faint); margin-bottom:6px;}
  th, td{border:1px solid var(--border); text-align:left; vertical-align:top; padding:8px 10px;}
  th{font-weight:600; background:var(--surface); font-size:12.5px; color:var(--muted);}
  td code{font-size:12.5px;}
  tr:nth-child(even) td{background:rgba(0,0,0,0.012);}

  code{
    background:var(--surface); border:1px solid var(--border);
    padding:1px 5px; border-radius:2px; font-size:0.88em; color:var(--accent-ink);
  }
  pre{
    background:var(--code-bg); color:var(--code-ink); border:1px solid var(--code-border);
    padding:14px 16px; border-radius:var(--radius); overflow-x:auto;
    font-size:13px; line-height:1.6; margin:0 0 14px; position:relative;
  }
  pre code{background:none; border:none; padding:0; color:inherit; font-size:1em;}
  .code-block{position:relative;}
  .code-block .copy-btn{
    position:absolute; top:8px; right:8px; color:var(--faint);
    background:rgba(255,255,255,0.06); z-index:2;
  }
  .code-block .copy-btn:hover{color:var(--code-ink); background:rgba(255,255,255,0.12);}

  .diagram{
    background:var(--surface); border:1px solid var(--border); border-radius:var(--radius);
    padding:16px; overflow-x:auto; margin:16px 0 24px;
  }
  .diagram pre{background:none; border:none; color:var(--ink); padding:0; margin:0; font-size:12.5px;}

  ol, ul{padding-left:22px; margin:0 0 14px;}
  li{margin-bottom:6px;}

  /* endpoint cards */
  .resource-group{margin-bottom:8px;}
  .resource-group > h3{
    display:flex; align-items:center; gap:10px; border-top:1px solid var(--border);
    padding-top:28px; margin-top:36px;
  }
  .resource-count{
    font-size:12px; color:var(--faint); font-weight:400;
    font-family:'IBM Plex Mono', monospace;
  }
  .endpoint{
    background:var(--surface); border:1px solid var(--border); border-radius:6px;
    padding:20px 22px 22px; margin:0 0 18px; scroll-margin-top:16px;
  }
  .endpoint-top{display:flex; align-items:center; gap:10px; margin-bottom:10px; flex-wrap:wrap;}
  .method{
    font-family:'IBM Plex Mono', monospace; font-size:11.5px; font-weight:600;
    padding:3px 8px; border-radius:3px; letter-spacing:0.03em; flex-shrink:0;
  }
  .method.get{color:var(--get); background:color-mix(in srgb, var(--get) 10%, white); border:1px solid color-mix(in srgb, var(--get) 30%, white);}
  .method.post{color:var(--post); background:color-mix(in srgb, var(--post) 10%, white); border:1px solid color-mix(in srgb, var(--post) 30%, white);}
  .method.patch{color:var(--patch); background:color-mix(in srgb, var(--patch) 12%, white); border:1px solid color-mix(in srgb, var(--patch) 32%, white);}
  .method.delete{color:var(--delete); background:color-mix(in srgb, var(--delete) 10%, white); border:1px solid color-mix(in srgb, var(--delete) 30%, white);}
  .endpoint-path{font-family:'IBM Plex Mono', monospace; font-size:14.5px; font-weight:500;}
  .endpoint-summary{color:var(--muted); font-size:14.5px; margin:0 0 16px;}
  .code-grid{display:grid; grid-template-columns:1fr 1fr; gap:12px;}
  .code-col-label{font-size:11px; color:var(--faint); font-weight:600; margin:0 0 6px; letter-spacing:0.02em;}

  /* status table inline chips */
  .http-code{font-family:'IBM Plex Mono', monospace; font-weight:600;}

  footer.page-footer{
    padding:36px 40px 60px; color:var(--faint); font-size:12.5px;
  }
  footer.page-footer .content-wrap{border-top:1px solid var(--border); padding-top:22px;}

  /* mobile */
  @media (max-width:900px){
    .sidebar{
      position:fixed; left:0; top:0; height:100dvh; z-index:40;
      transform:translateX(-100%); transition:transform 0.18s ease;
      width:80vw; max-width:320px; box-shadow:2px 0 18px rgba(0,0,0,0.15);
    }
    .sidebar.open{transform:translateX(0);}
    .sidebar-toggle{
      display:flex; align-items:center; gap:8px;
      position:sticky; top:0; z-index:30; background:var(--bg);
      border-bottom:1px solid var(--border); padding:14px 20px;
      font-size:13px; font-weight:600; color:var(--ink); cursor:pointer;
      border-left:none; border-right:none; border-top:none; width:100%;
      font-family:inherit;
    }
    .content-wrap{padding:0 20px;}
    header.hero{padding:32px 20px 28px;}
    section{padding:32px 20px;}
    .content-wrap > section{padding:32px 0;}
    h1.hero-title{font-size:30px;}
    .code-grid{grid-template-columns:1fr;}
    .scrim{
      display:none; position:fixed; inset:0; background:rgba(10,10,10,0.35); z-index:35;
    }
    .scrim.show{display:block;}
  }
  @media (min-width:901px){
    .sidebar-toggle{display:none !important;}
  }

  @media (prefers-reduced-motion:reduce){
    html{scroll-behavior:auto;}
    .sidebar{transition:none;}
  }
</style>
</head>
<body>

<div class="scrim" id="scrim"></div>

<div class="shell">
  <aside class="sidebar" id="sidebar" aria-label="Documentation navigation">
    <div class="sidebar-head">
      <p class="brand"><span class="brand-mark"></span><span class="brand-name">Nexa Commerce</span></p>
      <p class="brand-sub">REST API · v1.0 · OpenAPI 3.1</p>
      <div class="base-url-chip">
        <code id="base-url-text">api.nexacommerce.example.com/v1</code>
        <button class="copy-btn" data-copy="https://api.nexacommerce.example.com/v1" aria-label="Copy base URL">Copy</button>
      </div>
    </div>
    <nav class="toc" aria-label="Table of contents">
      <div class="toc-group">
        <a href="#overview">Overview</a>
        <a href="#getting-started">Getting started</a>
        <a href="#conventions">API conventions</a>
        <a href="#resource-model">Resource model</a>
        <a href="#order-lifecycle">Order lifecycle</a>
      </div>
      <div class="toc-group">
        <span class="toc-group-label">Endpoint reference</span>
        <a href="#endpoint-reference">All endpoints</a>
        <a href="#res-customers" class="endpoint-link"><span class="m m-post">5</span> Customers</a>
        <a href="#res-products" class="endpoint-link"><span class="m m-get">4</span> Products</a>
        <a href="#res-orders" class="endpoint-link"><span class="m m-post">5</span> Orders</a>
        <a href="#res-order-items" class="endpoint-link"><span class="m m-patch">3</span> Order items</a>
        <a href="#res-payments" class="endpoint-link"><span class="m m-post">3</span> Payments</a>
        <a href="#res-shipments" class="endpoint-link"><span class="m m-get">2</span> Shipments</a>
        <a href="#res-webhooks" class="endpoint-link"><span class="m m-post">3</span> Webhooks</a>
      </div>
      <div class="toc-group">
        <a href="#webhooks">Webhooks</a>
        <a href="#errors">Errors &amp; troubleshooting</a>
        <a href="#integration">Integration walkthrough</a>
        <a href="#design-decisions">Documentation approach</a>
        <a href="#appendix">API coverage</a>
      </div>
    </nav>
  </aside>

  <main>
    <button class="sidebar-toggle" id="sidebar-toggle" aria-expanded="false" aria-controls="sidebar">☰ Contents</button>

    <header class="hero" id="top">
      <div class="content-wrap">
        <p class="hero-eyebrow">Developer reference</p>
        <h1 class="hero-title">Nexa Commerce API v1</h1>
        <p class="hero-desc">A REST API for a fictional B2B commerce platform, covering customers, products, orders, payments, shipments, and webhooks.</p>
        <p class="hero-byline">Written by <strong>Gopala Krishna S.</strong> · Technical Writing Portfolio Sample</p>
        <div class="hero-stats">
          <div class="hero-stat"><b>25</b><span>HTTP operations</span></div>
          <div class="hero-stat"><b>6</b><span>core resources</span></div>
          <div class="hero-stat"><b>7</b><span>order states</span></div>
          <div class="hero-stat"><b>3.1</b><span>OpenAPI spec version</span></div>
        </div>
        <div class="hero-purpose">
          <h2 class="hero-purpose-title">Purpose of this work sample</h2>
          <p>Demonstrate senior-level technical writing skills across API information architecture, developer onboarding, resource reference, reusable API conventions, error documentation, business workflows, and integration guidance.</p>
          <p class="hero-disclaimer">Fictional product and API created for demonstration purposes. No real credentials, customer data, or production endpoints are represented.</p>
        </div>
      </div>
    </header>

    <div class="content-wrap">

    <section id="overview">
      <div class="section-head"><span class="section-num">01</span><h2>Product &amp; API overview</h2></div>
      <p class="section-intro">Nexa Commerce is a fictional cloud-based B2B commerce platform. Its REST API covers customer, product, order, payment, shipment, and webhook integrations.</p>
      <p>The API follows a practical business flow: a customer portal creates an order, payment is recorded, fulfillment progresses through shipment states, and webhooks keep downstream systems synchronized.</p>
      <h3>Audience</h3>
      <p>Backend developers, integration engineers, and solution architects connecting an ERP, storefront, or fulfillment system to Nexa Commerce.</p>
      <h3>Base URL</h3>
      <div class="code-block"><pre><code>https://api.nexacommerce.example.com/v1</code></pre><button class="copy-btn" data-copy="https://api.nexacommerce.example.com/v1">Copy</button></div>
      <h3>Core resources</h3>
      <table>
        <thead><tr><th>Resource</th><th>Purpose</th><th>Relationship</th></tr></thead>
        <tbody>
          <tr><td>Customer</td><td>Buyer or account profile</td><td>Customer → Orders</td></tr>
          <tr><td>Product</td><td>Sellable catalog item</td><td>Product → Order items</td></tr>
          <tr><td>Order</td><td>Commercial transaction</td><td>Order → Items / Payments / Shipments</td></tr>
          <tr><td>Payment</td><td>Payment attempt</td><td>Payment → Order</td></tr>
          <tr><td>Shipment</td><td>Fulfillment movement</td><td>Shipment → Order</td></tr>
          <tr><td>Webhook</td><td>Event subscription</td><td>Webhook → Events</td></tr>
        </tbody>
      </table>
    </section>

    <section id="getting-started">
      <div class="section-head"><span class="section-num">02</span><h2>Getting started</h2></div>
      <h3>Authentication</h3>
      <p>Send a bearer token with every authenticated request. Requests and responses use JSON.</p>
      <div class="code-block"><pre><code>curl https://api.nexacommerce.example.com/v1/customers \
  -H "Authorization: Bearer &lt;YOUR_ACCESS_TOKEN&gt;" \
  -H "Accept: application/json"</code></pre><button class="copy-btn" data-copy='curl https://api.nexacommerce.example.com/v1/customers -H "Authorization: Bearer <YOUR_ACCESS_TOKEN>" -H "Accept: application/json"'>Copy</button></div>
      <h3>Create your first customer</h3>
      <div class="code-block"><pre><code>curl -X POST https://api.nexacommerce.example.com/v1/customers \
  -H "Authorization: Bearer &lt;YOUR_ACCESS_TOKEN&gt;" \
  -H "Content-Type: application/json" \
  -d '{"name":"Acme Industrial Supplies","email":"ops@acme.example"}'</code></pre><button class="copy-btn" data-copy='curl -X POST https://api.nexacommerce.example.com/v1/customers -H "Authorization: Bearer <YOUR_ACCESS_TOKEN>" -H "Content-Type: application/json" -d {"name":"Acme Industrial Supplies","email":"ops@acme.example"}'>Copy</button></div>
    </section>

    <section id="conventions">
      <div class="section-head"><span class="section-num">03</span><h2>API conventions</h2></div>
      <h3>Pagination</h3>
      <p>Collection endpoints use cursor-based pagination. Treat the cursor as opaque — don't decode or construct it manually.</p>
      <div class="code-block"><pre><code>GET /orders?limit=25&amp;cursor=eyJjcmVhdGVkX2F0Ijoi...

{
  "data": [ ... ],
  "pagination": { "limit": 25, "next_cursor": "..." }
}</code></pre><button class="copy-btn" data-copy="GET /orders?limit=25&cursor=eyJjcmVhdGVkX2F0Ijoi...">Copy</button></div>
      <h3>Sorting and filtering</h3>
      <p>The default sort is <code>-created_at</code>. Resource-specific filters combine with logical AND. <code>created_after</code> and <code>created_before</code> accept RFC 3339 timestamps.</p>
      <h3>Idempotency</h3>
      <p>Order and payment creation accept an <code>Idempotency-Key</code> header so retries are safe to send.</p>
    </section>

    <section id="resource-model">
      <div class="section-head"><span class="section-num">04</span><h2>Resource model</h2></div>
      <p class="section-intro">Nexa Commerce models commerce as a small set of connected resources.</p>
      <div class="diagram"><pre>CUSTOMER  1 ───────── N  ORDER
                         │
                         ├── 1:N  ORDER ITEMS ── N:1 ── PRODUCT
                         ├── 1:N  PAYMENTS
                         └── 1:N  SHIPMENTS</pre></div>
      <h3>Resource snapshots</h3>
      <p>Order items preserve the product SKU, name, and unit price at the time of purchase, so later catalog changes never rewrite historical orders.</p>
      <h3>Identifier patterns</h3>
      <table>
        <thead><tr><th>Resource</th><th>Identifier prefix</th></tr></thead>
        <tbody>
          <tr><td>Customer</td><td><code>cus_...</code></td></tr>
          <tr><td>Product</td><td><code>prod_...</code></td></tr>
          <tr><td>Order</td><td><code>ord_...</code></td></tr>
          <tr><td>Order item</td><td><code>item_...</code></td></tr>
          <tr><td>Payment</td><td><code>pay_...</code></td></tr>
          <tr><td>Shipment</td><td><code>shp_...</code></td></tr>
          <tr><td>Webhook</td><td><code>wh_...</code></td></tr>
        </tbody>
      </table>
    </section>

    <section id="order-lifecycle">
      <div class="section-head"><span class="section-num">05</span><h2>Order lifecycle</h2></div>
      <p class="section-intro">The order state model makes business transitions explicit rather than implicit in application code.</p>
      <div class="diagram"><pre>DRAFT
  │
  ▼
PENDING ─────────────► CANCELLED
  │
  ▼
PAID
  │
  ▼
PROCESSING
  │
  ▼
SHIPPED
  │
  ▼
DELIVERED</pre></div>
      <div class="note"><strong>State rule —</strong> delivered and cancelled orders can't be edited. An invalid state transition returns <span class="http-code">409 Conflict</span> with code <code>INVALID_STATE</code>.</div>
      <p>Cancellation is a business action with side effects, not a data deletion — so the API models it as <code>POST /orders/{orderId}/cancel</code> rather than <code>DELETE</code>.</p>
    </section>

    <section id="endpoint-reference">
      <div class="section-head"><span class="section-num">06</span><h2>Complete endpoint reference</h2></div>
      <p class="section-intro">All 25 operations in Nexa Commerce v1, grouped by resource. Each entry follows the same order: method and path, purpose, parameters, then a sample request and response.</p>

      <div class="resource-group">
        <h3 id="res-customers">Customers <span class="resource-count">5 operations</span></h3>

        <article class="endpoint" id="endpoint-01">
          <div class="endpoint-top"><span class="method post">POST</span><span class="endpoint-path">/customers</span></div>
          <p class="endpoint-summary">Create a customer.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody><tr><td>body</td><td>object</td><td>Yes</td><td><code>name</code> and <code>email</code> are required.</td></tr></tbody></table>
          <p><strong>Response:</strong> <span class="http-code">201 Created</span></p>
          <div class="code-grid">
            <div><p class="code-col-label">Request</p><pre><code>{
  "name": "Acme Industrial Supplies",
  "email": "ops@acme.example",
  "phone": "+1-555-0100"
}</code></pre></div>
            <div><p class="code-col-label">Response</p><pre><code>{
  "id": "cus_01HZX8M4Y7",
  "name": "Acme Industrial Supplies",
  "email": "ops@acme.example",
  "status": "active"
}</code></pre></div>
          </div>
        </article>

        <article class="endpoint" id="endpoint-02">
          <div class="endpoint-top"><span class="method get">GET</span><span class="endpoint-path">/customers</span></div>
          <p class="endpoint-summary">List customers.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody>
            <tr><td>limit</td><td>integer</td><td>No</td><td>1–100; default 25.</td></tr>
            <tr><td>cursor</td><td>string</td><td>No</td><td>Opaque pagination cursor.</td></tr>
            <tr><td>status</td><td>enum</td><td>No</td><td>active, inactive, suspended.</td></tr>
            <tr><td>email</td><td>string</td><td>No</td><td>Exact email filter.</td></tr>
            <tr><td>external_id</td><td>string</td><td>No</td><td>Exact external identifier.</td></tr>
            <tr><td>created_after</td><td>string</td><td>No</td><td>RFC 3339 timestamp.</td></tr>
            <tr><td>created_before</td><td>string</td><td>No</td><td>RFC 3339 timestamp.</td></tr>
          </tbody></table>
          <p><strong>Response:</strong> <span class="http-code">200 OK</span></p>
          <p class="code-col-label">Response</p>
          <pre><code>{
  "data": [
    { "id": "cus_01HZX8M4Y7", "name": "Acme Industrial Supplies", "email": "ops@acme.example" }
  ],
  "pagination": { "limit": 25, "next_cursor": null }
}</code></pre>
        </article>

        <article class="endpoint" id="endpoint-03">
          <div class="endpoint-top"><span class="method get">GET</span><span class="endpoint-path">/customers/{customerId}</span></div>
          <p class="endpoint-summary">Retrieve a customer.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody><tr><td>customerId</td><td>string</td><td>Yes</td><td>Customer identifier matching <code>cus_...</code></td></tr></tbody></table>
          <p><strong>Response:</strong> <span class="http-code">200 OK</span></p>
          <pre><code>{
  "id": "cus_01HZX8M4Y7",
  "name": "Acme Industrial Supplies",
  "email": "ops@acme.example",
  "status": "active"
}</code></pre>
        </article>

        <article class="endpoint" id="endpoint-04">
          <div class="endpoint-top"><span class="method patch">PATCH</span><span class="endpoint-path">/customers/{customerId}</span></div>
          <p class="endpoint-summary">Update a customer.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody>
            <tr><td>customerId</td><td>string</td><td>Yes</td><td>Customer identifier.</td></tr>
            <tr><td>body</td><td>object</td><td>Yes</td><td>Any mutable customer field.</td></tr>
          </tbody></table>
          <p><strong>Response:</strong> <span class="http-code">200 OK</span></p>
          <div class="code-grid">
            <div><p class="code-col-label">Request</p><pre><code>{
  "phone": "+1-555-0199",
  "status": "active"
}</code></pre></div>
            <div><p class="code-col-label">Response</p><pre><code>{
  "id": "cus_01HZX8M4Y7",
  "name": "Acme Industrial Supplies",
  "phone": "+1-555-0199",
  "status": "active"
}</code></pre></div>
          </div>
        </article>

        <article class="endpoint" id="endpoint-05">
          <div class="endpoint-top"><span class="method delete">DELETE</span><span class="endpoint-path">/customers/{customerId}</span></div>
          <p class="endpoint-summary">Delete a customer.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody><tr><td>customerId</td><td>string</td><td>Yes</td><td>Customer identifier.</td></tr></tbody></table>
          <p><strong>Response:</strong> <span class="http-code">204 No Content</span> — no response body.</p>
        </article>
      </div>

      <div class="resource-group">
        <h3 id="res-products">Products <span class="resource-count">4 operations</span></h3>

        <article class="endpoint" id="endpoint-06">
          <div class="endpoint-top"><span class="method post">POST</span><span class="endpoint-path">/products</span></div>
          <p class="endpoint-summary">Create a product.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody><tr><td>body</td><td>object</td><td>Yes</td><td><code>sku</code>, <code>name</code>, <code>unit_price</code>, and <code>currency</code> are required.</td></tr></tbody></table>
          <p><strong>Response:</strong> <span class="http-code">201 Created</span></p>
          <div class="code-grid">
            <div><p class="code-col-label">Request</p><pre><code>{
  "sku": "IND-1001",
  "name": "Industrial Pump",
  "description": "Standard B2B pump",
  "unit_price": 125.00,
  "currency": "USD"
}</code></pre></div>
            <div><p class="code-col-label">Response</p><pre><code>{
  "id": "prod_01HZX9A2K1",
  "sku": "IND-1001",
  "name": "Industrial Pump",
  "status": "active",
  "unit_price": 125.00,
  "currency": "USD"
}</code></pre></div>
          </div>
        </article>

        <article class="endpoint" id="endpoint-07">
          <div class="endpoint-top"><span class="method get">GET</span><span class="endpoint-path">/products</span></div>
          <p class="endpoint-summary">List products.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody>
            <tr><td>limit</td><td>integer</td><td>No</td><td>1–100; default 25.</td></tr>
            <tr><td>cursor</td><td>string</td><td>No</td><td>Opaque pagination cursor.</td></tr>
            <tr><td>status</td><td>enum</td><td>No</td><td>active, inactive, discontinued.</td></tr>
            <tr><td>sku</td><td>string</td><td>No</td><td>Exact SKU filter.</td></tr>
            <tr><td>search</td><td>string</td><td>No</td><td>Search product name or description.</td></tr>
            <tr><td>created_after</td><td>string</td><td>No</td><td>RFC 3339 timestamp.</td></tr>
            <tr><td>created_before</td><td>string</td><td>No</td><td>RFC 3339 timestamp.</td></tr>
          </tbody></table>
          <p><strong>Response:</strong> <span class="http-code">200 OK</span></p>
          <pre><code>{
  "data": [
    { "id": "prod_01HZX9A2K1", "sku": "IND-1001", "name": "Industrial Pump", "status": "active" }
  ],
  "pagination": { "limit": 25, "next_cursor": null }
}</code></pre>
        </article>

        <article class="endpoint" id="endpoint-08">
          <div class="endpoint-top"><span class="method get">GET</span><span class="endpoint-path">/products/{productId}</span></div>
          <p class="endpoint-summary">Retrieve a product.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody><tr><td>productId</td><td>string</td><td>Yes</td><td>Product identifier matching <code>prod_...</code></td></tr></tbody></table>
          <p><strong>Response:</strong> <span class="http-code">200 OK</span></p>
          <pre><code>{
  "id": "prod_01HZX9A2K1",
  "sku": "IND-1001",
  "name": "Industrial Pump",
  "status": "active",
  "unit_price": 125.00,
  "currency": "USD"
}</code></pre>
        </article>

        <article class="endpoint" id="endpoint-09">
          <div class="endpoint-top"><span class="method patch">PATCH</span><span class="endpoint-path">/products/{productId}</span></div>
          <p class="endpoint-summary">Update a product.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody>
            <tr><td>productId</td><td>string</td><td>Yes</td><td>Product identifier.</td></tr>
            <tr><td>body</td><td>object</td><td>Yes</td><td>Mutable product fields.</td></tr>
          </tbody></table>
          <p><strong>Response:</strong> <span class="http-code">200 OK</span></p>
          <div class="code-grid">
            <div><p class="code-col-label">Request</p><pre><code>{
  "name": "Industrial Pump — Gen 2",
  "unit_price": 139.00
}</code></pre></div>
            <div><p class="code-col-label">Response</p><pre><code>{
  "id": "prod_01HZX9A2K1",
  "sku": "IND-1001",
  "name": "Industrial Pump — Gen 2",
  "unit_price": 139.00,
  "currency": "USD"
}</code></pre></div>
          </div>
        </article>
      </div>

      <div class="resource-group">
        <h3 id="res-orders">Orders <span class="resource-count">5 operations</span></h3>

        <article class="endpoint" id="endpoint-10">
          <div class="endpoint-top"><span class="method post">POST</span><span class="endpoint-path">/orders</span></div>
          <p class="endpoint-summary">Create an order.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody>
            <tr><td>Idempotency-Key</td><td>header</td><td>Yes</td><td>16–255 characters; reuse it for safe retries.</td></tr>
            <tr><td>body</td><td>object</td><td>Yes</td><td><code>customer_id</code>, <code>currency</code>, <code>items</code>, <code>billing_address</code>, and <code>shipping_address</code> are required.</td></tr>
          </tbody></table>
          <p><strong>Response:</strong> <span class="http-code">201 Created</span></p>
          <div class="code-grid">
            <div><p class="code-col-label">Request</p><pre><code>{
  "customer_id": "cus_01HZX8M4Y7",
  "currency": "USD",
  "items": [
    { "product_id": "prod_01HZX9A2K1", "quantity": 10 }
  ],
  "billing_address": {
    "line1": "100 Market Street",
    "city": "Austin",
    "state": "TX",
    "postal_code": "78701",
    "country": "US"
  },
  "shipping_address": { "...": "..." }
}</code></pre></div>
            <div><p class="code-col-label">Response</p><pre><code>{
  "id": "ord_01HZXA6D3P",
  "customer_id": "cus_01HZX8M4Y7",
  "status": "pending",
  "currency": "USD",
  "subtotal": 1250.00,
  "tax": 100.00,
  "shipping_cost": 25.00,
  "total": 1375.00
}</code></pre></div>
          </div>
        </article>

        <article class="endpoint" id="endpoint-11">
          <div class="endpoint-top"><span class="method get">GET</span><span class="endpoint-path">/orders</span></div>
          <p class="endpoint-summary">List orders.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody>
            <tr><td>limit</td><td>integer</td><td>No</td><td>1–100; default 25.</td></tr>
            <tr><td>cursor</td><td>string</td><td>No</td><td>Opaque pagination cursor.</td></tr>
            <tr><td>customer_id</td><td>string</td><td>No</td><td>Filter by customer.</td></tr>
            <tr><td>status</td><td>enum</td><td>No</td><td>draft, pending, paid, processing, shipped, delivered, cancelled.</td></tr>
            <tr><td>min_total</td><td>number</td><td>No</td><td>Minimum order total.</td></tr>
            <tr><td>max_total</td><td>number</td><td>No</td><td>Maximum order total.</td></tr>
            <tr><td>created_after</td><td>string</td><td>No</td><td>RFC 3339 timestamp.</td></tr>
            <tr><td>created_before</td><td>string</td><td>No</td><td>RFC 3339 timestamp.</td></tr>
            <tr><td>sort</td><td>string</td><td>No</td><td><code>created_at</code> or <code>-created_at</code>.</td></tr>
          </tbody></table>
          <p><strong>Response:</strong> <span class="http-code">200 OK</span></p>
          <pre><code>{
  "data": [
    { "id": "ord_01HZXA6D3P", "customer_id": "cus_01HZX8M4Y7", "status": "pending", "total": 1375.00 }
  ],
  "pagination": { "limit": 25, "next_cursor": null }
}</code></pre>
        </article>

        <article class="endpoint" id="endpoint-12">
          <div class="endpoint-top"><span class="method get">GET</span><span class="endpoint-path">/orders/{orderId}</span></div>
          <p class="endpoint-summary">Retrieve an order.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody><tr><td>orderId</td><td>string</td><td>Yes</td><td>Order identifier matching <code>ord_...</code></td></tr></tbody></table>
          <p><strong>Response:</strong> <span class="http-code">200 OK</span></p>
          <pre><code>{
  "id": "ord_01HZXA6D3P",
  "customer_id": "cus_01HZX8M4Y7",
  "status": "pending",
  "currency": "USD",
  "total": 1375.00,
  "items": []
}</code></pre>
        </article>

        <article class="endpoint" id="endpoint-13">
          <div class="endpoint-top"><span class="method patch">PATCH</span><span class="endpoint-path">/orders/{orderId}</span></div>
          <p class="endpoint-summary">Update an order.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody>
            <tr><td>orderId</td><td>string</td><td>Yes</td><td>Order identifier.</td></tr>
            <tr><td>body</td><td>object</td><td>Yes</td><td>Mutable fields such as addresses and metadata.</td></tr>
          </tbody></table>
          <p><strong>Response:</strong> <span class="http-code">200 OK</span></p>
          <div class="code-grid">
            <div><p class="code-col-label">Request</p><pre><code>{
  "shipping_address": {
    "line1": "200 Congress Ave",
    "city": "Austin",
    "state": "TX",
    "postal_code": "78701",
    "country": "US"
  }
}</code></pre></div>
            <div><p class="code-col-label">Response</p><pre><code>{
  "id": "ord_01HZXA6D3P",
  "status": "pending",
  "shipping_address": {
    "line1": "200 Congress Ave",
    "city": "Austin"
  }
}</code></pre></div>
          </div>
        </article>

        <article class="endpoint" id="endpoint-14">
          <div class="endpoint-top"><span class="method post">POST</span><span class="endpoint-path">/orders/{orderId}/cancel</span></div>
          <p class="endpoint-summary">Cancel an order.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody><tr><td>orderId</td><td>string</td><td>Yes</td><td>Order identifier.</td></tr></tbody></table>
          <p><strong>Response:</strong> <span class="http-code">200 OK</span></p>
          <pre><code>{
  "id": "ord_01HZXA6D3P",
  "status": "cancelled",
  "updated_at": "2026-09-12T09:02:00Z"
}</code></pre>
        </article>
      </div>

      <div class="resource-group">
        <h3 id="res-order-items">Order items <span class="resource-count">3 operations</span></h3>

        <article class="endpoint" id="endpoint-15">
          <div class="endpoint-top"><span class="method post">POST</span><span class="endpoint-path">/orders/{orderId}/items</span></div>
          <p class="endpoint-summary">Add an item to an order.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody>
            <tr><td>orderId</td><td>string</td><td>Yes</td><td>Order identifier.</td></tr>
            <tr><td>body</td><td>object</td><td>Yes</td><td><code>product_id</code> and <code>quantity</code> are required.</td></tr>
          </tbody></table>
          <p><strong>Response:</strong> <span class="http-code">201 Created</span></p>
          <div class="code-grid">
            <div><p class="code-col-label">Request</p><pre><code>{
  "product_id": "prod_01HZX9A2K1",
  "quantity": 5
}</code></pre></div>
            <div><p class="code-col-label">Response</p><pre><code>{
  "id": "item_01HZXB1N5K",
  "product_id": "prod_01HZX9A2K1",
  "sku": "IND-1001",
  "name": "Industrial Pump",
  "quantity": 5,
  "unit_price": 125.00,
  "subtotal": 625.00
}</code></pre></div>
          </div>
        </article>

        <article class="endpoint" id="endpoint-16">
          <div class="endpoint-top"><span class="method patch">PATCH</span><span class="endpoint-path">/orders/{orderId}/items/{itemId}</span></div>
          <p class="endpoint-summary">Update an order item's quantity.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody>
            <tr><td>orderId</td><td>string</td><td>Yes</td><td>Order identifier.</td></tr>
            <tr><td>itemId</td><td>string</td><td>Yes</td><td>Order item identifier.</td></tr>
            <tr><td>body</td><td>object</td><td>Yes</td><td><code>quantity</code> is mutable while the order is editable.</td></tr>
          </tbody></table>
          <p><strong>Response:</strong> <span class="http-code">200 OK</span></p>
          <div class="code-grid">
            <div><p class="code-col-label">Request</p><pre><code>{ "quantity": 8 }</code></pre></div>
            <div><p class="code-col-label">Response</p><pre><code>{
  "id": "item_01HZXB1N5K",
  "quantity": 8,
  "unit_price": 125.00,
  "subtotal": 1000.00
}</code></pre></div>
          </div>
        </article>

        <article class="endpoint" id="endpoint-17">
          <div class="endpoint-top"><span class="method delete">DELETE</span><span class="endpoint-path">/orders/{orderId}/items/{itemId}</span></div>
          <p class="endpoint-summary">Remove an item from an order.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody>
            <tr><td>orderId</td><td>string</td><td>Yes</td><td>Order identifier.</td></tr>
            <tr><td>itemId</td><td>string</td><td>Yes</td><td>Order item identifier.</td></tr>
          </tbody></table>
          <p><strong>Response:</strong> <span class="http-code">204 No Content</span> — no response body.</p>
        </article>
      </div>

      <div class="resource-group">
        <h3 id="res-payments">Payments <span class="resource-count">3 operations</span></h3>

        <article class="endpoint" id="endpoint-18">
          <div class="endpoint-top"><span class="method post">POST</span><span class="endpoint-path">/orders/{orderId}/payments</span></div>
          <p class="endpoint-summary">Create a payment attempt for an order.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody>
            <tr><td>orderId</td><td>string</td><td>Yes</td><td>Order identifier.</td></tr>
            <tr><td>Idempotency-Key</td><td>header</td><td>Yes</td><td>16–255 characters; reuse it for retries.</td></tr>
            <tr><td>body</td><td>object</td><td>Yes</td><td><code>amount</code>, <code>currency</code>, <code>method</code>, and <code>provider</code>.</td></tr>
          </tbody></table>
          <p><strong>Response:</strong> <span class="http-code">201 Created</span></p>
          <div class="code-grid">
            <div><p class="code-col-label">Request</p><pre><code>{
  "amount": 1375.00,
  "currency": "USD",
  "method": "purchase_order",
  "provider": "internal"
}</code></pre></div>
            <div><p class="code-col-label">Response</p><pre><code>{
  "id": "pay_01HZXC1M6N",
  "order_id": "ord_01HZXA6D3P",
  "amount": 1375.00,
  "currency": "USD",
  "status": "processing",
  "method": "purchase_order",
  "provider": "internal"
}</code></pre></div>
          </div>
        </article>

        <article class="endpoint" id="endpoint-19">
          <div class="endpoint-top"><span class="method get">GET</span><span class="endpoint-path">/orders/{orderId}/payments</span></div>
          <p class="endpoint-summary">List payments for an order.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody>
            <tr><td>orderId</td><td>string</td><td>Yes</td><td>Order identifier.</td></tr>
            <tr><td>limit</td><td>integer</td><td>No</td><td>1–100; default 25.</td></tr>
            <tr><td>cursor</td><td>string</td><td>No</td><td>Opaque pagination cursor.</td></tr>
            <tr><td>status</td><td>enum</td><td>No</td><td>pending, processing, succeeded, failed, cancelled.</td></tr>
            <tr><td>created_after</td><td>string</td><td>No</td><td>RFC 3339 timestamp.</td></tr>
            <tr><td>created_before</td><td>string</td><td>No</td><td>RFC 3339 timestamp.</td></tr>
          </tbody></table>
          <p><strong>Response:</strong> <span class="http-code">200 OK</span></p>
          <pre><code>{
  "data": [
    { "id": "pay_01HZXC1M6N", "order_id": "ord_01HZXA6D3P", "status": "processing", "amount": 1375.00 }
  ],
  "pagination": { "limit": 25, "next_cursor": null }
}</code></pre>
        </article>

        <article class="endpoint" id="endpoint-20">
          <div class="endpoint-top"><span class="method get">GET</span><span class="endpoint-path">/payments/{paymentId}</span></div>
          <p class="endpoint-summary">Retrieve a payment.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody><tr><td>paymentId</td><td>string</td><td>Yes</td><td>Payment identifier matching <code>pay_...</code></td></tr></tbody></table>
          <p><strong>Response:</strong> <span class="http-code">200 OK</span></p>
          <pre><code>{
  "id": "pay_01HZXC1M6N",
  "order_id": "ord_01HZXA6D3P",
  "status": "succeeded",
  "amount": 1375.00,
  "currency": "USD"
}</code></pre>
        </article>
      </div>

      <div class="resource-group">
        <h3 id="res-shipments">Shipments <span class="resource-count">2 operations</span></h3>

        <article class="endpoint" id="endpoint-21">
          <div class="endpoint-top"><span class="method get">GET</span><span class="endpoint-path">/orders/{orderId}/shipments</span></div>
          <p class="endpoint-summary">List shipments for an order.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody>
            <tr><td>orderId</td><td>string</td><td>Yes</td><td>Order identifier.</td></tr>
            <tr><td>limit</td><td>integer</td><td>No</td><td>1–100; default 25.</td></tr>
            <tr><td>cursor</td><td>string</td><td>No</td><td>Opaque pagination cursor.</td></tr>
            <tr><td>status</td><td>enum</td><td>No</td><td>pending, processing, shipped, delivered, cancelled.</td></tr>
            <tr><td>created_after</td><td>string</td><td>No</td><td>RFC 3339 timestamp.</td></tr>
            <tr><td>created_before</td><td>string</td><td>No</td><td>RFC 3339 timestamp.</td></tr>
          </tbody></table>
          <p><strong>Response:</strong> <span class="http-code">200 OK</span></p>
          <pre><code>{
  "data": [
    { "id": "shp_01HZXD7K3R", "order_id": "ord_01HZXA6D3P", "status": "shipped", "carrier": "Nexa Logistics", "tracking_number": "NX123456789" }
  ],
  "pagination": { "limit": 25, "next_cursor": null }
}</code></pre>
        </article>

        <article class="endpoint" id="endpoint-22">
          <div class="endpoint-top"><span class="method get">GET</span><span class="endpoint-path">/shipments/{shipmentId}</span></div>
          <p class="endpoint-summary">Retrieve a shipment.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody><tr><td>shipmentId</td><td>string</td><td>Yes</td><td>Shipment identifier matching <code>shp_...</code></td></tr></tbody></table>
          <p><strong>Response:</strong> <span class="http-code">200 OK</span></p>
          <pre><code>{
  "id": "shp_01HZXD7K3R",
  "order_id": "ord_01HZXA6D3P",
  "status": "shipped",
  "carrier": "Nexa Logistics",
  "tracking_number": "NX123456789"
}</code></pre>
        </article>
      </div>

      <div class="resource-group">
        <h3 id="res-webhooks">Webhooks <span class="resource-count">3 operations</span></h3>

        <article class="endpoint" id="endpoint-23">
          <div class="endpoint-top"><span class="method post">POST</span><span class="endpoint-path">/webhooks</span></div>
          <p class="endpoint-summary">Create a webhook subscription.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody><tr><td>body</td><td>object</td><td>Yes</td><td><code>url</code> and <code>events</code> are required; the URL must use HTTPS.</td></tr></tbody></table>
          <p><strong>Response:</strong> <span class="http-code">201 Created</span></p>
          <div class="code-grid">
            <div><p class="code-col-label">Request</p><pre><code>{
  "url": "https://erp.acme.example/webhooks/nexa",
  "events": ["order.paid", "order.shipped", "order.delivered"]
}</code></pre></div>
            <div><p class="code-col-label">Response</p><pre><code>{
  "id": "wh_01HZXE3P2D",
  "url": "https://erp.acme.example/webhooks/nexa",
  "events": ["order.paid", "order.shipped", "order.delivered"],
  "status": "active"
}</code></pre></div>
          </div>
        </article>

        <article class="endpoint" id="endpoint-24">
          <div class="endpoint-top"><span class="method get">GET</span><span class="endpoint-path">/webhooks</span></div>
          <p class="endpoint-summary">List webhook subscriptions.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody>
            <tr><td>limit</td><td>integer</td><td>No</td><td>1–100; default 25.</td></tr>
            <tr><td>cursor</td><td>string</td><td>No</td><td>Opaque pagination cursor.</td></tr>
            <tr><td>status</td><td>enum</td><td>No</td><td>active, inactive.</td></tr>
            <tr><td>sort</td><td>string</td><td>No</td><td><code>created_at</code> or <code>-created_at</code>.</td></tr>
          </tbody></table>
          <p><strong>Response:</strong> <span class="http-code">200 OK</span></p>
          <pre><code>{
  "data": [
    { "id": "wh_01HZXE3P2D", "url": "https://erp.acme.example/webhooks/nexa", "status": "active" }
  ],
  "pagination": { "limit": 25, "next_cursor": null }
}</code></pre>
        </article>

        <article class="endpoint" id="endpoint-25">
          <div class="endpoint-top"><span class="method delete">DELETE</span><span class="endpoint-path">/webhooks/{webhookId}</span></div>
          <p class="endpoint-summary">Delete a webhook subscription.</p>
          <h5>Parameters</h5>
          <table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Description</th></tr></thead>
          <tbody><tr><td>webhookId</td><td>string</td><td>Yes</td><td>Webhook identifier matching <code>wh_...</code></td></tr></tbody></table>
          <p><strong>Response:</strong> <span class="http-code">204 No Content</span> — no response body.</p>
        </article>
      </div>
    </section>

    <section id="webhooks">
      <div class="section-head"><span class="section-num">07</span><h2>Webhooks</h2></div>
      <p class="section-intro">Webhooks let downstream systems react to commerce events without repeatedly polling the API.</p>
      <h3>Recommended consumer pattern</h3>
      <ol>
        <li>Verify the delivery's security mechanism.</li>
        <li>Parse the event type and resource identifier.</li>
        <li>Persist the event or idempotency key before processing.</li>
        <li>Return a successful response quickly.</li>
        <li>Perform long-running work asynchronously.</li>
      </ol>
      <div class="note"><strong>Delivery guarantee —</strong> webhook delivery is at-least-once. Make event handling idempotent on your end.</div>
    </section>

    <section id="errors">
      <div class="section-head"><span class="section-num">08</span><h2>Errors &amp; troubleshooting</h2></div>
      <p class="section-intro">Errors use a stable envelope so clients can handle failures consistently across every resource.</p>
      <pre><code>{
  "error": {
    "code": "INVALID_REQUEST",
    "message": "One or more parameters are invalid.",
    "request_id": "req_01HZQ2M8F1",
    "details": [
      { "code": "INVALID_ENUM_VALUE", "message": "status must be active, inactive, or suspended.", "param": "status", "location": "query" },
      { "code": "VALUE_OUT_OF_RANGE", "message": "limit must be between 1 and 100.", "param": "limit", "location": "query" }
    ]
  }
}</code></pre>
      <h3>Status code guide</h3>
      <table>
        <thead><tr><th>HTTP</th><th>Meaning</th><th>Typical action</th></tr></thead>
        <tbody>
          <tr><td class="http-code">400</td><td>Malformed or unsupported request</td><td>Correct syntax or parameters.</td></tr>
          <tr><td class="http-code">401</td><td>Authentication failed</td><td>Check the bearer token.</td></tr>
          <tr><td class="http-code">403</td><td>Permission denied</td><td>Check required permissions.</td></tr>
          <tr><td class="http-code">404</td><td>Resource not found</td><td>Verify the identifier and environment.</td></tr>
          <tr><td class="http-code">409</td><td>Business state conflict</td><td>Refresh state; retry only if valid.</td></tr>
          <tr><td class="http-code">422</td><td>Valid shape, failed validation</td><td>Correct field-level validation errors.</td></tr>
          <tr><td class="http-code">429</td><td>Rate limit exceeded</td><td>Wait for <code>Retry-After</code> and retry.</td></tr>
          <tr><td class="http-code">500 / 503</td><td>Server or service failure</td><td>Retry with backoff when appropriate.</td></tr>
        </tbody>
      </table>
      <h3>Rate limiting</h3>
      <p>The API permits 60 requests per minute. Responses may include <code>X-RateLimit-Limit</code>, <code>X-RateLimit-Remaining</code>, and <code>Retry-After</code>.</p>
    </section>

    <section id="integration">
      <div class="section-head"><span class="section-num">09</span><h2>End-to-end integration walkthrough</h2></div>
      <p class="section-intro">A realistic integration combines synchronous API calls with asynchronous events.</p>
      <div class="diagram"><pre>1  POST /customers
        │
        ▼
2  POST /orders
        │
        ▼
3  POST /orders/{orderId}/payments
        │
        ├──── webhook: order.paid ────► ERP
        │
        ▼
4  GET /orders/{orderId}/shipments
        │
        └──── webhook: order.delivered ─► ERP</pre></div>
      <h3>Integration guidance</h3>
      <p>Use API responses for immediate state and webhooks for asynchronous state changes. Avoid building critical workflows around polling alone.</p>
    </section>

    <section id="design-decisions">
      <div class="section-head"><span class="section-num">10</span><h2>Documentation approach</h2></div>
      <h3>Endpoint-first reference</h3>
      <p>Every endpoint follows the same reading order: method and path, then purpose, parameters, request, and response — so a reader can scan and compare operations quickly.</p>
      <h3>Centralized conventions</h3>
      <p>Pagination, sorting, filtering, validation, errors, rate limits, and authentication are each defined once as API-wide conventions rather than repeated per endpoint.</p>
      <h3>Business-aware guidance</h3>
      <p>The documentation explains behavior that can't be inferred from HTTP verbs alone — order cancellation, editable order states, payment processing, and historical item snapshots.</p>
      <h3>Machine-readable foundation</h3>
      <p>A companion OpenAPI 3.1 specification provides reusable parameters, schemas, responses, security definitions, and resource-specific collection schemas.</p>
    </section>

    <section id="appendix">
      <div class="section-head"><span class="section-num">—</span><h2>Appendix: API coverage</h2></div>
      <table>
        <thead><tr><th>Resource area</th><th>Operations</th></tr></thead>
        <tbody>
          <tr><td>Customers</td><td>5 — create, list, retrieve, update, delete</td></tr>
          <tr><td>Products</td><td>4 — create, list, retrieve, update</td></tr>
          <tr><td>Orders</td><td>5 — create, list, retrieve, update, cancel</td></tr>
          <tr><td>Order items</td><td>3 — add, update, remove</td></tr>
          <tr><td>Payments</td><td>3 — create, list by order, retrieve</td></tr>
          <tr><td>Shipments</td><td>2 — list by order, retrieve</td></tr>
          <tr><td>Webhooks</td><td>3 — create, list, delete</td></tr>
          <tr><td><strong>Total</strong></td><td><strong>25 HTTP operations</strong></td></tr>
        </tbody>
      </table>
    </section>

    </div>
  </main>
</div>

<footer class="page-footer">
  <div class="content-wrap">
    Nexa Commerce · REST API v1 · Developer documentation work sample · Fictional product, created for portfolio purposes.
  </div>
</footer>

<script>
(function(){
  // Copy-to-clipboard
  document.querySelectorAll('.copy-btn').forEach(function(btn){
    btn.addEventListener('click', function(){
      var text = btn.getAttribute('data-copy');
      if(!text){
        var pre = btn.previousElementSibling;
        text = pre ? pre.textContent : '';
      }
      navigator.clipboard.writeText(text).then(function(){
        var original = btn.textContent;
        btn.textContent = 'Copied';
        setTimeout(function(){ btn.textContent = original; }, 1400);
      }).catch(function(){});
    });
  });

  // Mobile sidebar toggle
  var sidebar = document.getElementById('sidebar');
  var toggle = document.getElementById('sidebar-toggle');
  var scrim = document.getElementById('scrim');
  function closeSidebar(){
    sidebar.classList.remove('open');
    scrim.classList.remove('show');
    toggle.setAttribute('aria-expanded', 'false');
  }
  function openSidebar(){
    sidebar.classList.add('open');
    scrim.classList.add('show');
    toggle.setAttribute('aria-expanded', 'true');
  }
  if(toggle){
    toggle.addEventListener('click', function(){
      sidebar.classList.contains('open') ? closeSidebar() : openSidebar();
    });
  }
  scrim.addEventListener('click', closeSidebar);
  sidebar.querySelectorAll('a').forEach(function(a){
    a.addEventListener('click', function(){ if(window.innerWidth <= 900) closeSidebar(); });
  });

  // Scrollspy for top-level sections
  var links = Array.prototype.slice.call(document.querySelectorAll('.toc > .toc-group > a, .toc > .toc-group > a.endpoint-link'));
  var topLinks = Array.prototype.slice.call(document.querySelectorAll('.toc-group > a:not(.endpoint-link)'));
  var sections = topLinks.map(function(l){
    var id = l.getAttribute('href').slice(1);
    return document.getElementById(id);
  }).filter(Boolean);

  var observer = new IntersectionObserver(function(entries){
    entries.forEach(function(entry){
      var id = entry.target.id;
      var link = document.querySelector('.toc a[href="#' + id + '"]');
      if(!link) return;
      if(entry.isIntersecting){
        topLinks.forEach(function(l){ l.classList.remove('active'); });
        link.classList.add('active');
      }
    });
  }, { rootMargin: '-20% 0px -70% 0px', threshold: 0 });

  sections.forEach(function(s){ observer.observe(s); });
})();
</script>
</body>
</html>

