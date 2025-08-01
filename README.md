# Traefik Reverse Proxy with Docker Compose

This project provides a simple setup for running [Traefik](https://traefik.io/) as a reverse proxy using Docker Compose. It includes example configurations for routers and middlewares, and is ready to use with Let's Encrypt for automatic SSL certificate management.

## Features

- **Traefik as a reverse proxy** for your Docker containers
- **Automatic HTTPS** with Let's Encrypt (using `acme.json`)
- **Custom routers and middlewares** configuration
- **Cloudflare DNS challenge** support (see `cf-token`)

## Project Structure

```
├── acme.json              # Stores Let's Encrypt certificates (must be chmod 600)
├── cf-token               # Cloudflare API token for DNS challenge (optional)
├── docker-compose.yaml    # Docker Compose file to run Traefik
├── traefik.yaml           # Main Traefik static configuration
├── config/
│   ├── middlewares.yaml   # Dynamic middlewares configuration
│   └── routers.yaml       # Dynamic routers configuration
```

## Getting Started

1. **Clone this repository:**
   ```zsh
   git clone https://github.com/jershbytes/traefik.git
   cd traefik
   ```

2. **Create and secure `acme.json`:**
   ```zsh
   touch acme.json
   chmod 600 acme.json
   ```

3. **Add your Cloudflare API token:**
   - Place your token in the `cf-token` file if using Cloudflare DNS challenge.

4. **Configure your domains and services:**
   - Edit `config/routers.yaml` and `config/middlewares.yaml` as needed.

5. **Start Traefik:**
   ```zsh
   docker-compose up -d
   ```

6. **Access the Traefik dashboard:**
   - The dashboard URL and credentials are defined in your configuration files.

## Configuration Files

- **`traefik.yaml`**: Static configuration for Traefik (entrypoints, providers, certificatesResolvers, etc.)
- **`config/routers.yaml`**: Dynamic router definitions (routes, services, TLS, etc.)
- **`config/middlewares.yaml`**: Dynamic middleware definitions (redirects, security headers, etc.)

## Security Notes

- Ensure `acme.json` is readable only by Traefik (chmod 600).
- Do not commit sensitive tokens or secrets to version control.

## References

- [Traefik Documentation](https://doc.traefik.io/traefik/)
- [Docker Compose](https://docs.docker.com/compose/)

---
Feel free to customize this setup for your own needs!
