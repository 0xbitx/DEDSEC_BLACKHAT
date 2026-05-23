
<p align="center">
<img src="https://github.com/user-attachments/assets/9fcb7d81-0b9c-4551-a94b-bed9ae526307", width="400", height="400">
</p>

<h1 align="center">BLACKHAT</h1> <h4 align="center">OPSEC BROWSER - Your digital ghost. No cookies. No cache. No fingerprints.</h4>

## DESCRIPTION

BlackHat is a privacy-hardened browser automation tool that launches browser through an obfs4 Tor proxy with complete anti-fingerprinting, zero persistence, and automatic bridge fetching.

It is designed for operational security (OPSEC) professionals, red teamers, OSINT investigators, and privacy-conscious individuals who require a disposable, anonymous browsing environment that leaves no trace on the host system.

#### Unlike standard Tor Browser, BlackHat goes several steps further:

   * **Fully ephemeral sessions** – Every browsing session is completely isolated. No cookies, no cache, no history, no local storage, no service workers, and no persistent data of any kind survive after the browser window closes. Each session is a fresh, clean slate.

   * **Deep anti-fingerprinting** – BlackHat doesn't just block fingerprinting attempts; it actively spoofs them. Every session randomly generates a unique browser fingerprint including user agent, timezone, language preferences, screen resolution behavior, and platform identifiers. This prevents tracking across sessions and makes each session appear as a different device.

   * **Obfs4 bridge integration** – Standard Tor is easily detected and blocked by deep packet inspection (DPI) systems used in countries with heavy internet censorship. BlackHat automatically fetches fresh obfs4 bridges from the Tor Project's BridgeDB, then routes all traffic through these bridges to make Tor traffic indistinguishable from random internet noise. This bypasses DPI, country-level blocks, and corporate firewalls.

   * **Pre-compromised system protection** – If your host system is compromised or monitored, BlackHat's zero-persistence approach ensures no browsing history, credentials, or session data remains on disk. The temporary profile is created in RAM-backed /tmp and destroyed when the browser closes.

   * **Leak-proof configuration** – WebRTC is completely disabled to prevent IP address leaks through STUN requests. DNS prefetching is turned off. DNS requests are sent over the Tor proxy instead of the host system's DNS. Geolocation, camera, microphone, notifications, and desktop capture are all denied by default.

   * **Ad and tracker blocking** – Multiple blocklists are applied including StevenBlack's unified hosts file, EasyList, and EasyPrivacy. This blocks telemetry, analytics, fingerprinting scripts, and malicious domains at the network level.

   * **Hardened browser settings** – JavaScript is disabled by default (can be toggled per-site with tsh command). Canvas reading is blocked. WebGL is disabled. Client hints are stripped. XSS auditing is enabled. Mixed content downloads from HTTPS pages are blocked. The Chromium sandbox is fully enabled for process isolation.

   * **Automatic bridge fetching** – No manual bridge configuration required. BlackHat scrapes fresh obfs4 bridges directly from the Tor Project's BridgeDB API and MOAT protocol, falling back to a curated list of known-good bridges if the automatic fetch fails. This ensures connectivity even in heavily censored environments.

   * **System-level timezone spoofing** – BlackHat doesn't just lie to the browser; it sets the TZ environment variable to match the spoofed profile, ensuring even system-level time APIs return the fake timezone.

#### Every session is:

  - Ephemeral – No cookies, cache, or history saved. The browser profile exists only in RAM and is destroyed on exit.

  - Spoofed – Randomized fingerprints including user agent, timezone, language, and platform identifiers change with every session.

  - Leak-proof – WebRTC disabled, DNS over proxy, geolocation blocked, camera and microphone denied, notifications disabled.

  - Censorship-resistant – Obfs4 bridges bypass deep packet inspection (DPI), country blocks, and corporate firewalls.

  - Zero persistence – No data written to disk. No traces left behind. Even the Tor data directory is temporary.

  - Non-deterministic – Each session is cryptographically random, making tracking across sessions impossible.

BlackHat is not a replacement for the Tor Browser Bundle in all use cases, but it offers significantly stronger anti-fingerprinting and zero-persistence guarantees for users who prioritize operational security and disposable browsing over convenience.

## Use Cases
| Use Case	| Why BlackHat |
|-----------|------------------|
| OSINT investigations	| Conduct research without leaving traces or building a fingerprint profile that can be tracked across sessions |
| Red team operations	| Access command-and-control panels, leak sites, and dark web resources without exposing team infrastructure |
| Censorship circumvention	| Browse freely from countries with internet restrictions (China, Russia, Iran, etc.) |
| Whistleblowing	| Securely access anonymous drop sites without leaving forensic evidence on the host machine |
| Journalism	| Research sensitive topics without building a trackable browsing profile that could be subpoenaed |
| Privacy activism	| Demonstrate strong operational security practices in training environments |

## Technical Deep Dive: Obfs4 Protocol

Obfs4 (The Obfourscator) is a pluggable transport that transforms Tor traffic into random-looking noise. It uses:

   - Elligator 2 – Cryptographic mapping that makes public keys indistinguishable from random bytes

   - NaCl secret boxes – Strong encryption using Poly1305 and XSalsa20

   - Constant-rate padding – Randomized packet sizes and timing to defeat traffic analysis

   - Full key exchange – Complete forward secrecy for every connection

BlackHat automates the entire obfs4 setup process that would otherwise require manual bridge configuration.
Fingerprint Randomization

### Each session generates a unique fingerprint by randomizing:

| Component	| Randomization Method |
|-----------|---------------|
| User agent |	Random selection from 30+ real device signatures (Windows/Linux/macOS/Android/iOS) |
| Platform |	Matches user agent device type |
| Timezone |	Matches region of selected language (50+ timezones) |
| Language |	Random selection from 100+ language/region combinations |
| Screen behavior |	Window size set to match common resolutions for spoofed device |


### INSTALLATION
    git clone https://github.com/0xbitx/DEDSEC_BLACKHAT.git
    cd DEDSEC_BLACKHAT
    sudo apt-get install -y tor obfs4proxy qutebrowser
    chmod +x dedsec_blackhat
    ./dedsec_blackhat
    
### TESTED ON FOLLOWING
* Kali Linux 
* Parrot OS 
  
## Legal Disclaimer

This tool is intended for educational and security research purposes only. Unauthorized usage may be illegal in your jurisdiction. The author is not responsible for any misuse of this tool.
