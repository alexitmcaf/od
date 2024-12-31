# Use the official Odoo image as the base
FROM odoo:16.0

# Switch to root for package installation
USER root

# Install necessary utilities and dependencies
RUN apt-get update \
    && apt-get install -y iputils-ping python3-pip libpq-dev build-essential \
    && pip3 install psycopg2-binary \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Add custom Odoo modules
COPY ./addons /mnt/extra-addons

# Switch back to odoo user
USER odoo

# Expose the port Odoo will run on
EXPOSE 8069

# Set default environment variables
ENV DB_HOST=db \
    DB_PORT=5432 \
    DB_USER=odoo \
    DB_PASSWORD=odoo16@2022

# Set the entrypoint for the container
ENTRYPOINT ["/entrypoint.sh"]
