# Use the official Odoo image as the base
FROM odoo:16.0

# Install necessary utilities
RUN apt-get update && apt-get install -y iputils-ping && rm -rf /var/lib/apt/lists/*

# Copy your custom addons and configuration as needed
COPY ./addons /mnt/extra-addons
COPY ./etc/odoo.conf /etc/odoo/

# Expose the port Odoo will run on
EXPOSE 8069

# Set the entrypoint for the container
ENTRYPOINT ["/entrypoint.sh"]
