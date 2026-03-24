---
title: "Your Guest Welcome Dashboard"
layout: "single"
---

<div id="guest-card" style="max-width:450px; margin:20px auto; font-family:sans-serif; background:#fff; border:1px solid #eee; border-radius:16px; padding:25px; box-shadow:0 10px 25px rgba(0,0,0,0.05);">
    <h2 style="margin-top:0; text-align:center;">Karibu Nyumbani! 🇰🇪</h2>
    <p style="text-align:center; color:#666; font-size:0.9rem;">Everything you need for a 5-star stay.</p>

<div style="display:grid; gap:20px; margin-top:25px;">
    <div style="padding:15px; background:#f0f7ff; border-radius:12px;">
        <strong style="display:block; color:#0070f3; margin-bottom:5px;">📶 WiFi Access</strong>
        <span id="g-wifi" style="font-size:1.1rem; font-weight:bold;">---</span>
        <div style="margin-top:10px; font-size:0.85rem; color:#555;">
            <strong>Provider:</strong> <span id="g-provider">---</span>
        </div>
    </div>
    <div style="padding:15px; background:#fff9e6; border-radius:12px;">
        <strong style="display:block; color:#b8860b; margin-bottom:5px;">💡 Electricity Token</strong>
        <span id="g-token" style="font-size:1.1rem; font-weight:bold; letter-spacing:1px;">---</span>
    </div>
    <div style="padding:15px; background:#f4f4f4; border-radius:12px;">
        <strong style="display:block; color:#333; margin-bottom:5px;">🕚 Checkout Time</strong>
        <span id="g-checkout" style="font-size:1.1rem; font-weight:bold;">---</span>
    </div>
    <div style="padding:15px; border:1px dashed #ddd; border-radius:12px;">
        <strong style="display:block; color:#d32f2f; margin-bottom:5px;">🍕 Local Recommendations</strong>
        <span id="g-food" style="font-size:0.9rem; line-height:1.4;">---</span>
    </div>
</div>
</div>

<script>
    // 1. Grab the encoded data from the URL
    const params = new URLSearchParams(window.location.search);
    const rawData = params.get('data');

    if (rawData) {
        try {
            // 2. Decode the Base64 data
            const data = JSON.parse(atob(rawData));

            // 3. Inject it into the page
            document.getElementById('g-wifi').innerText = data.w || "See Router Sticker";
            document.getElementById('g-provider').innerText = data.p || "Not specified";
            document.getElementById('g-token').innerText = data.t || "Pre-paid by Host";
            document.getElementById('g-checkout').innerText = data.c || "10:00 AM";
            document.getElementById('g-food').innerText = data.f || "Ask host for favorites!";
        } catch (e) {
            console.error("Error decoding guest data", e);
        }
    }
</script>
