Home Lab Infrastructure

Personal home lab used for networking, monitoring, security, media, and self-hosting experiments.
Designed for learning, stability, and future expansion (SOC tooling, reverse proxy, GitOps).

Network Overview

LAN: 192.168.1.0/24

Primary DNS: Pi-hole

Reverse Proxy: Caddy (planned)

Service Discovery: Local DNS using .home

Access: SSH (key-based authentication)

Core Systems
Pi-hole (DNS and Admin UI)

Hostname: pihole

IP Address: 192.168.1.234

Role:

Network-wide DNS

Ad and tracker blocking

Local DNS records for home lab services

Services:

pihole-FTL (DNS and web backend)

Admin Interface:

http://192.168.1.234:8000/admin

Notes:

Web interface is served directly by Pi-hole FTL

HTTPS disabled internally (to be handled by Caddy)

Source of .home domain resolution

Prometheus (Primary Linux Server)

Hostname: Prometheus

IP Address: 192.168.1.28

Role:

Main Linux server

Git operations

Monitoring and orchestration hub

Capabilities:

SSH (ED25519 key authentication)

GitHub access via SSH

Docker host

Running Containers:

homepage – home lab dashboard

jellyfin – media server

filebrowser – web-based file access

Notes:

SSH agent configured with id_ed25519

Acts as the GitOps control point

Mothership (Primary Workstation)

Hostname: Mothership

IP Address: 192.168.1.123

Role:

Daily driver workstation

Administration and monitoring

Capabilities:

SSH client

Web access to all internal services

Notes:

Trusted management endpoint for the lab

Sisyphus (Auxiliary Node)

Hostname: Sisyphus

IP Address: 192.168.1.167

Role:

Secondary system

Planned Use:

Security tooling

Testing and staging workloads

Services
Homepage (Dashboard)

Host: Prometheus

Port: 3000

URL: http://192.168.1.28:3000

Purpose:

Central landing page for lab services

Jellyfin

Host: Prometheus

Port: 8096

Purpose:

Media streaming and management

FileBrowser

Host: Prometheus

Purpose:

Web-based file management interface

Security Model

SSH key-only authentication

No password-based SSH access

Multiple SSH keys segmented by device

Internal services bound to the LAN

HTTPS to be terminated by Caddy

DNS and Naming

Internal Domain: .home

Resolver: Pi-hole

Status:

IP-based access is functional

Local domain records managed in Pi-hole

Reverse proxy integration pending

Git and Configuration Management

GitHub Access: SSH (id_ed25519)

Primary Host: Prometheus

Use Cases:

Version control for infrastructure configs

Home lab documentation

Future GitOps workflows

Roadmap

Deploy Caddy as a reverse proxy

Enable HTTPS for all internal services

Access services via service.home

Centralized logging and metrics

Security monitoring (Suricata, Wazuh)

GitOps-style deployment

Notes

This home lab prioritizes clarity, debuggability, and incremental hardening over convenience or automation shortcuts.
