# 🛡️ Containerized Pi-hole Deployment via Docker Compose

A robust, lightweight, and easily maintainable network-wide ad-blocking and DNS management setup using **Pi-hole v6** inside a **Docker** container.

---

## 🚀 Features
* **Network-wide Protection:** Blocks ads, trackers, and malicious domains at the DNS level.
* **Containerized Infrastructure:** Deployed using Docker Compose for seamless scaling, backup, and isolation.
* **Resource Efficient:** Runs on low-power hardware (like a Raspberry Pi) 24/7 without breaking a sweat.
* **Modern v6 Architecture:** Utilizing the latest Pi-hole v6 release with streamlined configuration and management.

---

## 📂 Project Structure

```text
.
├── docker-compose.yml    # Main configuration file for Docker containers
└── README.md             # Project documentation

```

## ⚙️ Configuration (docker-compose.yml)

Here is the blueprint configuration used to spin up the container:

```yaml
services:
  pihole:
    container_name: pihole
    image: pihole/pihole:latest
    ports:
      - "53:53/tcp"
      - "53:53/udp"
      - "80:80/tcp"
    environment:
      - TZ=Europe/Berlin
    volumes:
      - './etc-pihole:/etc/pihole'
      - './etc-dnsmasq.d:/etc/dnsmasq.d'
    restart: unless-stopped

```
---

## 🛠️ Quick Start Guide

1. Clone or download this repository to your Docker host (e.g., Raspberry Pi).
2. Spin up the container using Docker Compose:
```bash
   docker compose up -d
```
3. Set a secure password for the web interface inside the container:
```bash
   docker exec -it pihole pihole setpassword
```
4. Access your admin dashboard at http://<your-pi-ip>/admin.
