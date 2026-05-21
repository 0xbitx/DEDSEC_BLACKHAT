# Internet Privacy and Tracking Overview

When you browse the internet, a lot more than your IP address can be used to identify or correlate activity. Some of it is technical metadata, some is behavioral.

---

# Network Identifiers

## IP Address

Your public IP is one of the biggest identifiers.

It can reveal:

- Approximate location
- ISP/mobile carrier
- Whether you’re using a VPN, datacenter, or residential connection

Law enforcement can often subpoena:

- ISP subscriber records
- VPN logs (if they exist)
- Connection timestamps

---

## DNS Requests

If your DNS traffic is not encrypted, your provider or network operator can see domains you visit.

Privacy-focused options:

- DNS over HTTPS (DoH)
- DNS over TLS (DoT)

---

## Browser Fingerprinting

Even without cookies, browsers expose a surprisingly unique combination of traits:

- Screen size
- Operating system
- Fonts
- GPU/WebGL info
- Timezone
- Installed extensions
- Canvas rendering behavior
- Audio stack quirks

This can create a semi-unique fingerprint.

---

# Tracking Mechanisms

## Cookies

Websites use cookies for:

- Login sessions
- Analytics
- Ad tracking
- Cross-site tracking

Third-party ad networks can correlate activity across many websites.

---

## Local Storage and Cache

Browsers store:

- Session tokens
- Cached resources
- IndexedDB data
- Service workers

Even after deleting cookies, traces can remain.

---

## Account Linkage

Logging into accounts strongly connects identity to browsing activity.

Examples:

- Email accounts
- Social media
- Cloud sync
- Phone numbers

One login can correlate an entire browsing session.

---

# Device-Level Identifiers

## MAC Address

MAC addresses mostly stay local, but they can still be logged by:

- Wi-Fi networks
- Routers
- Enterprise monitoring systems

Modern phones often use MAC randomization on Wi-Fi.

---

## Device Identifiers

Mobile apps may access:

- Advertising IDs
- Push notification tokens
- Device model identifiers
- Serial-related identifiers

Apps usually track users more aggressively than browsers.

---

# Metadata and Behavioral Signals

## Timing Correlation

Even if content is encrypted, timing patterns matter:

- When you connect
- Session duration
- Traffic bursts

Correlation attacks can sometimes link users across systems.

---

## Behavioral Fingerprinting

Patterns can identify users through:

- Typing rhythm
- Mouse movement
- Scrolling behavior
- Language patterns
- Active hours

---

# Common Operational Mistakes

People often expose themselves through:

- Reusing usernames
- Reusing emails
- Logging into personal accounts while using privacy tools
- Uploading images with metadata
- Browser extension leaks
- VPN disconnect leaks
- Using the same writing style everywhere

---

# Useful Defensive Privacy Practices

## Browser Hygiene

- Keep browsers updated
- Limit extensions
- Use separate browser profiles
- Block third-party cookies

---

## Network Privacy

- Use trusted VPNs carefully
- Prefer HTTPS everywhere
- Use encrypted DNS

---

## Compartmentalization

Separate:

- Personal accounts
- Work accounts
- Research activity
- Testing environments

---

## Metadata Awareness

Strip metadata from files and images before sharing:

- GPS coordinates
- Camera information
- Timestamps

---

## Device Security

- Full-disk encryption
- Strong passwords
- Multi-factor authentication (MFA)
- Regular updates

---

# Final Note

Privacy is usually less about one magic tool and more about reducing the number of signals that can be linked together over time.
