# Use the official Odoo image as the base
FROM odoo:16.0

# Create and set permissions for the addons directory
RUN mkdir -p /mnt/extra-addons && chown -R odoo:odoo /mnt/extra-addons

# Copy addons and configuration files into the container
COPY ./addons /mnt/extra-addons
COPY ./etc /etc/odoo/

# Set the environment variable for the Odoo config file
ENV ODOO_CONF=/etc/odoo/odoo.conf

# Add healthcheck
HEALTHCHECK --interval=30s --timeout=5s --start-period=30s --retries=3 \
    CMD curl --fail http://localhost:8069/web/login || exit 1

# Expose the port Odoo will run on
EXPOSE 8069

# Set the entrypoint and default command
ENTRYPOINT ["/entrypoint.sh"]
CMD ["odoo"]
