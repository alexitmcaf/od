# Use the official Odoo image as the base
FROM odoo:16.0

# Ensure /mnt/extra-addons exists and is accessible
RUN mkdir -p /mnt/extra-addons && chown -R odoo:odoo /mnt/extra-addons

# Copy your custom addons into the container
ARG CACHE_BUSTER=1
RUN ls -la .
RUN ls -la ./addons
RUN ls -la /mnt/extra-addons
COPY ./addons /mnt/extra-addons
RUN ls -la /mnt/extra-addons

# Copy your Odoo configuration file into the container
COPY odoo.conf /etc/odoo/

# Set the environment variable for the Odoo config file
ENV ODOO_CONF=/etc/odoo/odoo.conf

# Optional: Add healthcheck
HEALTHCHECK --interval=30s --timeout=5s --start-period=30s --retries=3 \
    CMD curl --fail http://localhost:8069 || exit 1

# Expose the port Odoo will run on
EXPOSE 8069

# Set the entrypoint for the container
ENTRYPOINT ["/entrypoint.sh"]
