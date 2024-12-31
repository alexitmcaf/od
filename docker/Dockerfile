# Use the official Odoo image as the base
FROM odoo:16.0

# Switch to root for package installation
USER root

# Install necessary utilities
RUN apt-get update \
    && apt-get install -y iputils-ping \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Switch back to odoo user
USER odoo

# Expose the port Odoo will run on
EXPOSE 8069

# Set the entrypoint for the container
ENTRYPOINT ["/entrypoint.sh"]
