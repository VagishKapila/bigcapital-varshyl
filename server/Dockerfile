# BigCapital Server — Railway Production
# Extends the official image to:
# 1. Create the symlink for migration path resolution
# 2. Run migrations on startup before the server starts
# 3. Start the NestJS server

FROM bigcapitalhq/server:latest

USER root

# Create symlink: /app/src/database -> /app/packages/server/src/database
# CLI uses process.cwd() (=/app) to find src/database/system/migrations
RUN mkdir -p /app/src && \
    ln -sf /app/packages/server/src/database /app/src/database && \
    chown -R nodejs:nodejs /app/src

USER nodejs
WORKDIR /app

# Run system + tenant migrations (idempotent), then start server
# Using ; not && so server starts even if migrations already applied
CMD ["/bin/sh", "-c", "node packages/server/dist/cli.js system:migrate:latest; node packages/server/dist/cli.js tenants:migrate:latest; node packages/server/dist/main.js"]
