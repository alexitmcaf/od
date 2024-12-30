# Use the official Odoo image as the base
FROM odoo:16.0

# Ensure /mnt/extra-addons exists and is accessible
RUN mkdir -p /mnt/extra-addons && chown -R odoo:odoo /mnt/extra-addons

# Debugging: List the build context directory
ARG CACHE_BUSTER=1
RUN echo "Debugging build context..." && ls -la .

# Copy your custom addons into the container
COPY ./addons /mnt/extra-addons
RUN echo "Debugging addons directory..." && ls -la /mnt/extra-addons

# Copy your Odoo configuration file into the container
RUN echo "Debugging etc directory..." && ls -la ./etc
COPY ./etc/odoo.conf /etc/odoo/
RUN echo "Debugging /etc/odoo directory..." && ls -la /etc/odoo

# Set the environment variable for the Odoo config file
ENV ODOO_CONF=/etc/odoo/odoo.conf

# Optional: Add healthcheck
HEALTHCHECK --interval=30s --timeout=5s --start-period=30s --retries=3 \
    CMD curl --fail http://localhost:8069 || exit 1

# Expose the port Odoo will run on
EXPOSE 8069

# Set the entrypoint for the container
ENTRYPOINT ["/entrypoint.sh"]
