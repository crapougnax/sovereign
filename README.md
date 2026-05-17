# Sovereign

Sovereign is an autonomous server management CLI designed to deploy and manage a complete, self-hosted infrastructure using Podman. It supports two primary deployment modes: **Personal** (User-only) and **Infrastructure** (Shared/System).

## Key Features

- **Multi-Mode Deployment**: 
  - **User Mode (Rootless)**: Everything runs within a standard user's home directory. Perfect for a single-user personal server.
  - **System Mode (Infrastructure)**: Deploy Traefik as a system-level service (managed by `root` and `systemd`) to handle global routing for multiple users on the same host.
- **Standalone CLI**: Install once, manage everything.
- **GitHub Backed**: Recipes are fetched dynamically from your central GitHub repository.
- **Security First**: Optimized for rootless Podman environments.
- **Centralized Config**: A single `.env` file manages your entire stack.

## Quick Install

```bash
curl -fsSL https://raw.githubusercontent.com/crapougnax/sovereign/main/install.sh | bash
```

## Getting Started

### 1. Choice of Deployment Mode

- **Personal Server**: Run commands as your standard user. Everything will be stored in `~/.sovereign/`.
- **Shared Server**: Install Traefik as `root` (`sudo sovereign install traefik`) to manage ports 80/443 globally.

### 2. Basic Workflow

1. **Setup**: Run `sovereign setup` to initialize your configuration.
2. **Configure**: Edit your `.env` (in `~/.sovereign/` or `/etc/sovereign/`) to add your API tokens.
3. **Deploy Core**: 
   ```bash
   # System mode (Infrastructure)
   sudo sovereign install traefik
   
   # User mode (Personal)
   sovereign install core/smtp
   ```
4. **Add Apps**:
   ```bash
   sovereign install immich
   sovereign install nextcloud
   ```

## License

GNU AGPL-v3. See [LICENSE](LICENSE) for details.
