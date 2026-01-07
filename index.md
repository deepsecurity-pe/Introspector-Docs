---
title: Home
layout: home
---

# 🧠 Introspector Framework


> **Swiss-Army Knife for deep HTTP exploitation..**


Introspector Framework is a powerful, modular platform designed to help offensive security professionals observe, manipulate, and exploit HTTP-based interactions. It acts as a trap, a dynamic payload host, and a precision response controller — all wrapped in REPL interface, zero noise and total visibility.

---

## 🎯 What is Introspector?

* Advanced HTTP listeners  
* Dynamic payload host  
* Precision-by-Design PoC backend

It's all of them — in one REPL-driven, black-box ready, offensive framework.

Read the full documentation and feature list here.

---

## 🔥 Key Features

- 🛰️ **Passive HTTP Listener**
  - Captures all HTTP methods from any source
  - Real-time logging: timestamp, IP, headers, path, full body
  - Handles traffic behind proxies (Cloudflare, Akamai, etc.)
  - Save your Introspector session with `--persist` flag

- 🔌 **Multi-Port Listening**
  - Launch listeners dynamically: `listen 8080`, `listen 8888`, etc.
  - Supports multiple ports simultaneously (e.g. 80, 8080, 1337)
  - Run callbacks from different attack vectors in parallel
  - Use `listeners` to view all active ports

- 🧪 **Run Custom Payloads from the Console**
  - Run modules on demand: `run svg-bomb`, `run xxe`, `run csv-injector`, etc.
  - Generates endpoints like `/run/xyz123.svg` from static templates
  - Served with ready to use Exploits

- 🧬 **Host Custom Server Response**
  - Response Templates loaded from `/hostedfiles/`
  - Host files on demand: `file upload /home/user/iframe.html`, `file upload /root/secret.txt`, etc.
  - Easy to create new response vectors with correct `Content-Type` for exploitation use
  - Supports `.xml`, `.svg`, `.jpg`, `.png`, among others

- 🌑 **Web UI for Logs (Dark Mode)**
  - Access full logs via `/logs-<id>`
  - Displays Request Method, HTTP Headers, URI, and request body in real-time
  - IP Whois and IP Country Auto-Detect

- 🧭 **Passive Redirect Scanner**
  - Auto-Detect if the requests recieved follow redirects.
  - Traps in `/robots.txt`, `/favicon.ico`, or custom endpoints
  - Toggle with `scanner on` and `scanner off`

---

## 📦 Installation

```bash
git clone https://github.com/deepsecurity-pe/Introspector.git
cd introspector-framework
pip3 install -r requirements.txt
sudo python3 Introspector.py
```

---
### 🚀 Example Session

```
sudo python3 Introspector.py --persist session01
```

```
╔════════════════════════════════════════════════════════════════════╗
║                 INTROSPECTOR FRAMEWORK  —  HTTP OPS TOOL          ║
║           Passive Traps · Callback Intel · Payload Hosting        ║
╚════════════════════════════════════════════════════════════════════╝

   [LOG UI]       http://127.0.0.1/logs-x7j2l9d
   [PORTS]        80
   [CLOAK MODE]   OFF
   [GEOIP]        OK
   [PERSIST]      ON
   [EVENTS]       12
   [PAYLOADS]     8
   [HOSTED]       /hostedfiles/<id>.<ext>


[introspector]> run svg-bomb
[+] Created /run/x1f92c.svg (Content-Type: image/svg+xml)

[introspector]> listen 8888
[+] Listener started on port 8888

[introspector]> listeners
[=] Active listener ports:
 - 80
 - 8888

[introspector]> file upload /root/iframe.html
[+] hosted file from /root/iframe.html -> [ ID: 5u8mkt6i ]
    URL: /hostedfiles/5u8mkt6i.html

[introspector]> file list
[=] Registered paths:
 -  /hostedfiles/5u8mkt6i.html -> [ ID: 5u8mkt6i ]

[introspector]> scanner on
[+] Follow redirect scanner ENABLED

[introspector]> exit
[!] Exiting...
```

---

### 🧠 Available Commands

```
run <xxe|svg-bomb|jpg-file|csv-injector>     Generate a module from template
listen <port>                                Start a new listener on the given port
listeners                                    Show all currently active listener ports
list                                         Show all registered run modules
file upload <path>                           Host an existing file under /hostedfiles/<id>.<ext>
file unload <id>                             Unhost a previously hosted file by id
file list                                    List all hosted files
scanner on                                   Enable follow redirect scanner
scanner off                                  Disable follow redirect scanner
persist                                      Resume a previous Introspector session
help                                         Show this help message
exit                                         Terminate Introspector
```

---

### 🧬 Use Cases

- 🛰️ **Blind SSRF detection**  
  Use `.svg`, `.xml` or `.png` modules to trigger callbacks inside restricted networks.

- 🎯 **Redirect exploitation**  
  Test if targets follow redirects to sensitive paths like `/robots.txt`, `/favicon.ico`, or crafted URLs.

- 💥 **Payload delivery for injection attacks**  
  Serve dynamic content (XSS, open redirect payloads, malicious SVG) with full control over headers and content-type.

- 🧪 **Live PoC testing backend**  
  Host payloads and observe results in real-time, without needing a separate infrastructure.

- 🔍 **Beacon & callback tracking**  
  Detect image process from bots, previews, or sandbox environments

---

[Just the Docs]: https://just-the-docs.github.io/just-the-docs/
[GitHub Pages]: https://docs.github.com/en/pages
[README]: https://github.com/just-the-docs/just-the-docs-template/blob/main/README.md
[Jekyll]: https://jekyllrb.com
[GitHub Pages / Actions workflow]: https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/
[use this template]: https://github.com/just-the-docs/just-the-docs-template/generate
