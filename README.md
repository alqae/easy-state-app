
# 🏠 easy-state-app

**easy-state-app** is a platform to publish and view rental listings.
The system is split into multiple services, all exposed securely through **Nginx** with SSL and custom subdomains.

---

## 🔗 Services Overview

| Subdomain              | Internal Service | Port | Purpose                              |
| ---------------------- | ---------------- | ---- | ------------------------------------ |
| `mongo.easystate.info` | `mongo_express`  | 8081 | Web panel to manage MongoDB          |
| `api.easystate.info`   | `api`            | 8080 | Backend API for the application      |
| `easystate.info`       | `web`            | 80   | Frontend web interface for end users |

---

## 🔐 Security

All services are served over **HTTPS**.
SSL settings are centralized in `/etc/nginx/ssl.conf` to keep configuration consistent and secure.

---

## ⚙️ Notes

* `client_max_body_size 26M;` is enabled on the API to allow uploads up to 26 MB.
* Each service runs in its own container and is proxied by Nginx.
