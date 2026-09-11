# TLS, HTTP/2 & QUIC Security Lab

## Overview

Analysis of encrypted web communication using TLS 1.2, HTTP/2, TLS 1.3 and QUIC/HTTP/3 in an isolated Linux lab environment.

The project focuses on secure web-server configuration, packet-level handshake analysis, certificate trust, protocol negotiation and transport-layer disruption using Wireshark, Nginx, Caddy, OpenSSL and curl.

## Implementation and testing

* Configured Nginx with HTTPS and a self-signed RSA 4096-bit certificate
* Captured and analysed the TLS 1.2 handshake in Wireshark
* Identified Client Hello, Server Hello, certificate exchange, ECDHE key exchange and encrypted Application Data
* Verified use of `TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384`
* Identified X25519 as the elliptic curve used during key exchange
* Enabled HTTP/2 and verified `h2` negotiation using ALPN
* Configured Caddy v2 for QUIC and HTTP/3 using TLS 1.3
* Analysed QUIC Initial, Handshake and Protected Payload packets
* Compared first and repeated QUIC connections for 0-RTT and 1-RTT behaviour
* Used Firefox TLS key logging to decrypt TLS 1.3 traffic and inspect a public certificate chain
* Compared a self-signed certificate with a trusted CA-based certificate chain
* Tested TCP RST injection using `hping3`, Scapy and `tcpkill`
* Demonstrated successful connection disruption using valid TCP sequence numbers
* Used ARP spoofing to establish a MITM position and observe active TCP session parameters

## Key findings

TLS 1.2 used TCP followed by a separate TLS handshake, while QUIC used UDP and integrated TLS 1.3 directly into the protocol.

HTTP/2 negotiation was confirmed through ALPN, while QUIC reduced the number of round trips required before encrypted communication could begin.

No clear 0-RTT application-data transmission was observed in the QUIC capture, although the repeated connection completed slightly faster.

The TCP RST tests also demonstrated that encrypted communication can be interrupted at the transport layer without breaking the TLS encryption itself.

## Evidence and limitations

The presentation includes configuration output, terminal captures and Wireshark evidence from the lab.

The demonstrated evidence includes TLS and QUIC handshakes, cipher-suite negotiation, certificate analysis, HTTP/2 ALPN negotiation, QUIC traffic, TCP RST injection and MITM traffic inspection.

The project does not claim that TLS encryption was compromised. The RST demonstrations targeted the underlying TCP connection.

A clear 0-RTT transfer was not captured, so successful 0-RTT application-data transmission is not claimed.

## Presentation

View the full presentation (PDF):

[tls-http2-quic-security-lab.pdf](./tls-http2-quic-security-lab.pdf)
