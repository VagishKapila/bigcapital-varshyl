# BigCapital Migration Runner
# The CLI uses process.cwd() to resolve src/database/system/migrations.
# The image has migrations at /app/packages/server/src/database/ NOT /app/src/database/.
# Fix: symlink /app/src/database -> /app/packages/server/src/database
# so CLI finds them at the expected path when run from WORKDIR /app.

FROM bigcapitalhq/server:latest

USER root

# Create symlink so /app/src/database resolves to where migrations actually live
RUN mkdir -p /app/src && \
    ln -sf /app/packages/server/src/database /app/src/database

WORKDIR /app

# Run both migration sets then sleep (Railway needs process alive for log capture)
CMD node packages/server/dist/cli.js system:migrate:latest && \
    node packages/server/dist/cli.js tenants:migrate:latest && \
    echo "=== ALL MIGRATIONS COMPLETE ===" && \
    sleep 600
