# Worktrees for Applications with Services

This guide provides additional setup steps when working with worktrees for projects that run services (web apps with HTTP servers, docker-compose services, etc.).

## When to Use This Guide

Use these instructions after following the main worktree setup in [SKILL.md](SKILL.md) **only if**:
- The project has `.env*` files in the main directory
- The project runs services like web servers, databases, or docker-compose

If the project is a library or CLI tool without a `.env` file, skip these instructions entirely.

## Copy Environment Files

Before configuring ports and starting services, copy any `.env*` files from the main working directory:

```bash
cp ../../.env* .
```

This ensures the worktree has the necessary environment configuration to run the application. Environment files are typically gitignored and won't be available in the new worktree otherwise.

## Port Allocation

To avoid conflicts when running multiple instances of the app in parallel worktrees, each worktree needs its own set of ports.

### Port Scanning

Use the provided script to find available ports starting from **9090**:

```bash
# Run the port allocation script from the worktrees skill
# Note: This script is located in the worktrees skill directory, not in the project repo
ports=($(bash scripts/allocate-ports.sh))

# Assign ports to variables (using 1-based indexing for zsh compatibility) For example if the project has a server and minio:
SERVER_PORT=${ports[1]}
MINIO_PORT=${ports[1]}
```

**Important:**
- Ports don't need to be consecutive - the script finds the next available port until it has 4
- The array uses 1-based indexing (zsh style) for compatibility
- The `scripts/` directory is part of the worktrees skill, not your project repository

### Update .env File

Once ports are allocated, update the `.env` file with the new values:

```bash
# Update SERVER_ADDRESS (note the : prefix)
sed -i '' "s|^SERVER_ADDRESS=.*|SERVER_ADDRESS=:${SERVER_PORT}|" .env

# Update BASE_URL
sed -i '' "s|^BASE_URL=.*|BASE_URL=http://localhost:${SERVER_PORT}|" .env
```

and so on, depending on the project.

## Starting Services

After updating the `.env` file, start the services. Podman compose up etc, following the instructions in the project's README / CLAUDE.md.

## Stopping Services

When stopping work in a worktree or cleaning up, shutdown the services. Podman compose down.

## Port Tracking

Ports are stored **only** in each worktree's `.env` file - there is no central registry. When you need to find which ports a worktree is using, read its `.env` file:

```bash
grep -E "^(SERVER_ADDRESS|MINIO_PORT)=" .worktrees/<branch-name>/.env
```

## Example Complete Workflow

```bash
# 1. Create worktree (from main skill.md)
git worktree add .worktrees/feature-auth -b feature-auth
cd .worktrees/feature-auth

# 2. Copy .env files
cp ../../.env* .

# 3. Allocate ports using the script
ports=($(bash scripts/allocate-ports.sh))
SERVER_PORT=${ports[1]}
MINIO_PORT=${ports[2]}
# Example allocation: 9090, 9091, 9092, 9093

# 4. Update .env with allocated ports
sed -i '' "s|^SERVER_ADDRESS=.*|SERVER_ADDRESS=:${SERVER_PORT}|" .env
sed -i '' "s|^MINIO_PORT=.*|MINIO_PORT=${MINIO_PORT}|" .env

# 5. Start services
podman compose up -d

# 6. Report to user
echo "Worktree created at .worktrees/feature-auth"
echo "App running at http://localhost:${SERVER_PORT}"
echo "MinIO S3 at http://localhost:${MINIO_PORT}"
echo "Services started successfully"

# Later: Stop services
podman compose down
```
