# Scraping G.O.A.T. 🐐

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

> A curated list of the **Greatest Of All Time (G.O.A.T.)** tools, engines, stealth browsers, TLS impersonators, and reverse-engineering utilities for modern web scraping.

Modern websites deploy sophisticated anti-bot protections: TLS fingerprinting (JA3/JA4), HTTP/2 frame analysis, Canvas/WebGL probing, behavioral analysis, and Cloudflare Turnstile challenges. Standard scrapers running stock `requests` or vanilla Puppeteer get blocked instantly.

This list tracks the tools that actually work against modern defenses.

---

## Contents

- [Full-Scale Frameworks & Spiders](#full-scale-frameworks--spiders)
- [HTTP Clients & TLS/JA3 Impersonation](#http-clients--tlsja3-impersonation)
- [Stealth Browsers & Anti-Detect Automation](#stealth-browsers--anti-detect-automation)
- [AI-Native Scraping & LLM Markdown Extractors](#ai-native-scraping--llm-markdown-extractors)
- [Parsers & Element Extractors](#parsers--element-extractors)
- [Fingerprint Generation & Spoofing](#fingerprint-generation--spoofing)
- [Anti-Bot Bypasses & Solvers](#anti-bot-bypasses--solvers)
- [Proxy Management & Traffic Routing](#proxy-management--traffic-routing)
- [DevTools, Interception & Reverse Engineering](#devtools-interception--reverse-engineering)
- [Testbenches & Bot Detectors](#testbenches--bot-detectors)

---

## Full-Scale Frameworks & Spiders

*Heavyweight frameworks designed for multi-page crawls, concurrency, and pipeline management.*

- [Scrapling](https://github.com/D4Vinci/Scrapling) (Python) - Fast scraping framework combining HTTP requests, stealth browsers, automated Turnstile/Interstitial solving, adaptive element tracking, and an MCP server for AI agents.
- [Crawlee](https://github.com/apify/crawlee) / [Crawlee Python](https://github.com/apify/crawlee-python) (Node.js / Python) - Apify's web scraping and crawling library. Handles proxy management, session pools, automated retries, and crawler queues.
- [Scrapy](https://github.com/scrapy/scrapy) (Python) - The industry standard asynchronous crawling framework. Extremely mature ecosystem with item pipelines, middlewares, and spider contracts.
- [Colly](https://github.com/gocolly/colly) (Go) - Elegant, fast, and concurrent scraping framework for Golang. Handles asynchronous callbacks, job queues, and automatic rate limiting.
- [Ferret](https://github.com/MontFerret/ferret) (Go) - Declarative web scraping system using Ferret Query Language (AQL) to automate browser interaction and data extraction.

---

## HTTP Clients & TLS/JA3 Impersonation

*Clients that mimic real browser TLS handshakes (ciphers, extensions, curves) and HTTP/2 settings to bypass network-level fingerprinting.*

- [curl-impersonate](https://github.com/lexiforest/curl-impersonate) (C) - A modified `curl` build that mimics the TLS and HTTP/2 fingerprints of major browsers (Chrome, Edge, Safari, Firefox) at the packet level.
- [curl-cffi](https://github.com/lexiforest/curl-cffi) (Python) - Python bindings for curl-impersonate. Drop-in replacement for `requests` or `httpx` with native JA3/JA4 browser impersonation and HTTP/3 support.
- [tls-client](https://github.com/bogdanfinn/tls-client) (Go) - Advanced HTTP library for Go built on uTLS to impersonate browser TLS handshakes and HTTP/2 fingerprinting.
- [CycleTLS](https://github.com/Danny-Dasilva/CycleTLS) (JS/TS / Go) - TLS fingerprint spoofer for Node.js and Go. Bypasses TLS fingerprint verification on Cloudflare, Akamai, and DataDome.
- [HTTPX](https://github.com/encode/httpx) (Python) - Next-generation HTTP client with sync and async APIs, HTTP/2 support, and strict connection pooling.

---

## Stealth Browsers & Anti-Detect Automation

*Headless automation frameworks patched to remove DevTools leaks, CDC flags, and runtime automation artifacts.*

- [Patchright](https://github.com/kaliiiiiiiiii/patchright) (Python / JS) - Undetected Playwright fork. Patches runtime CDP leaks, `Runtime.enable`, and DevTools detection vectors directly in browser binaries.
- [Camoufox](https://github.com/daijro/camoufox) (C++ / Python) - Anti-detect browser engine built directly into a customized Firefox build. Injects realistic hardware noise, fonts, and WebGL parameters at the C++ level.
- [DrissionPage](https://github.com/g1879/DrissionPage) (Python) - Hybrid driver combining requests and browser automation. Can switch seamlessly between HTTP requests and DOM control without webdriver signatures.
- [nodriver](https://github.com/ultrafunkamsterdam/nodriver) (Python) - Successor to undetected-chromedriver. Asynchronous, native Chrome controller communicating directly via CDP without `chromedriver`.
- [rebrowser-patches](https://github.com/rebrowser/rebrowser-patches) (Node.js) - Open-source patch suite for Puppeteer and Playwright to eliminate `Runtime.Enable` leaks and bypass modern bot detection engines.
- [puppeteer-extra-plugin-stealth](https://github.com/berstend/puppeteer-extra/tree/master/packages/puppeteer-extra-plugin-stealth) (JS) - The classic stealth plugin for Puppeteer that established evasions for `navigator.webdriver`, chrome runtime, permissions, and plugin arrays.

---

## AI-Native Scraping & LLM Markdown Extractors

*Tools converting raw web pages into clean, token-efficient Markdown, structured JSON, or schemas designed for LLM prompts and agent workflows.*

- [Crawl4AI](https://github.com/unclecode/crawl4ai) (Python) - Open-source, LLM-friendly web crawler that extracts structured, cleaned Markdown with chunking, media removal, and browser automation.
- [Firecrawl](https://github.com/mendableai/firecrawl) (TypeScript) - Turn entire websites into clean Markdown or structured JSON for LLM applications. Handles proxies, JavaScript rendering, and sitemap crawling.
- [Trafilatura](https://github.com/adbar/trafilatura) (Python) - State-of-the-art web text discovery and extraction library. Strips boilerplates, navigation chrome, and advertisements with high precision.
- [Readability.js](https://github.com/mozilla/readability) / [readability-lxml](https://github.com/buriy/python-readability) (JS / Python) - The standalone version of the readability engine behind Firefox Reader View.
- [html2text](https://github.com/Alir3z4/html2text) (Python) - Converts HTML into clean, formatted ASCII text and Markdown.

---

## Parsers & Element Extractors

*Ultra-fast HTML/XML parser engines for high-throughput DOM parsing.*

- [Selectolax](https://github.com/rushter/selectolax) (Python / C) - Blazing fast Python binding for Modest and Lexbor C engines. Up to 20x faster than BeautifulSoup and lxml for large DOM trees.
- [Parsel](https://github.com/scrapy/parsel) (Python) - The extraction engine extracted from Scrapy. Allows extracting data using CSS selectors, XPath expressions, and regular expressions.
- [Cheerio](https://github.com/cheeriojs/cheerio) (Node.js) - Fast, flexible, and lean implementation of core jQuery designed specifically for the server.
- [lxml](https://github.com/lxml/lxml) (Python) - Mature, battle-tested Pythonic binding for libxml2 and libxslt with full XPath 1.0 support.
- [goquery](https://github.com/PuerkitoBio/goquery) (Go) - Brings jQuery-like syntax and selection to the Go language, based on Go's `net/html`.

---

## Fingerprint Generation & Spoofing

*Libraries creating consistent, statistically valid hardware and browser profiles to prevent behavioral clustering.*

- [Browserforge](https://github.com/daijro/browserforge) (Python) - Intelligent browser fingerprint generator. Synthesizes statistically plausible combinations of User-Agents, HTTP headers, viewport dimensions, and hardware specs based on real-world distributions.
- [Fingerprint Injector](https://github.com/apify/fingerprint-suite) (Node.js) - Injects realistic browser fingerprints directly into Playwright and Puppeteer pages to avoid canvas, audio, and WebGL discrepancies.
- [Faker](https://github.com/joke2k/faker) (Python) - Generates randomized user-agents, addresses, and user identity data for scraper test runs.

---

## Anti-Bot Bypasses & Solvers

*Tools and helper proxies for solving or passing Cloudflare, CAPTCHAs, and challenge scripts.*

- [FlareSolverr](https://github.com/FlareSolverr/FlareSolverr) (Python / Docker) - Proxy server that handles Cloudflare and DDoS-GUARD challenge pages using Chromium and returns validated cookies.
- [Cloudscraper](https://github.com/VeNoMouS/cloudscraper) (Python) - Python module that bypasses Cloudflare's anti-bot page (legacy JS challenge engine).
- [Capsolver-Python](https://github.com/capsolver/capsolver-python) / [2Captcha-Python](https://github.com/2captcha/2captcha-python) - Official SDKs for programmatic solving of reCAPTCHA v2/v3, hCaptcha, Turnstile, and AWS WAF captchas via API services.

---

## Proxy Management & Traffic Routing

*Proxy managers, connection cyclers, and traffic rotators.*

- [proxy-chain](https://github.com/apify/proxy-chain) (Node.js) - Node.js proxy server with support for SSL, authentication, upstream proxy chaining, and custom IP rotation logic.
- [Mitmproxy](https://github.com/mitmproxy/mitmproxy) (Python) - An interactive SSL/TLS-capable intercepting HTTP proxy for monitoring, modifying, and replaying web traffic.
- [Mubeng](https://github.com/kitabisa/mubeng) (Go) - An automated IP rotator and proxy checker that runs as a local proxy server and rotates outbound IP on every request.
- [ProxyPool](https://github.com/jhao104/proxy_pool) (Python) - Automated scraper that crawls, validates, and stores working public proxy lists in Redis.

---

## DevTools, Interception & Reverse Engineering

*Tools to capture, inspect, and translate internal web API endpoints into native scraping code.*

- [curlconverter](https://github.com/curlconverter/curlconverter) (Web / CLI) - Converts raw `curl` commands (copied from Chrome/Firefox DevTools network tab) into Python, Go, Node.js, Rust, and C# code.
- [Whistle](https://github.com/avwo/whistle) (Node.js) - Cross-platform web debugging proxy tool based on Node.js with rule-based traffic modification.
- [mitmproxy2swagger](https://github.com/alufers/mitmproxy2swagger) (Python) - Automatically reverse-engineers REST APIs by converting mitmproxy captures into OpenAPI/Swagger specifications.
- [HAR Extractor](https://github.com/c4milo/har-extractor) - CLI tool to dump and extract cookies, payloads, and request headers from browser HAR files.

---

## Testbenches & Bot Detectors

*Benchmark websites to test your scraper's stealth score, fingerprint leaks, and anti-bot evasions.*

- [CreepJS](https://github.com/abrahamjuliot/creepjs) ([creepjs-api](https://abrahamjuliot.github.io/creepjs/)) - The gold standard test for browser fingerprint consistency, worker leaks, and headless tells.
- [Bot Sannysoft](https://bot.sannysoft.com/) - Classic detection testbench verifying `webdriver` properties, Chrome plugins, user-agent consistency, and permissions.
- [BrowserScan](https://www.browserscan.net/) - Tests IP reputation, WebRTC leaks, Canvas noise, and hardware consistency.
- [Incolumitas Bot Detection](https://deviceandbrowserinfo.com/are_you_a_bot) - Modern test checking TCP/IP fingerprinting, canvas randomness, and behavioral signals.

---

## Contributing

Suggestions and contributions are welcome:

1. Fork the repository.
2. Add the tool to the appropriate category with a concise, factual description.
3. Keep entries focused on tools that are actively maintained or historically significant.
4. Submit a pull request.

---

## License

MIT © [Marchiori](https://github.com/contamuito)
