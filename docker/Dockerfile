# Use the official Odoo image as the base
FROM odoo:16.0

# Switch to root for package installation
USER root

# Add the PostgreSQL APT repository and key
RUN apt-get update && apt-get install -y wget gnupg \
    && wget -qO - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add - \
    && echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list

# Install necessary utilities and dependencies
RUN apt-get update \
    && apt-get install -y iputils-ping python3-pip libpq-dev=17.2-1.pgdg110+1 build-essential \
    && pip3 install psycopg2-binary \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Switch back to the odoo user
USER odoo

# Expose the Odoo port
EXPOSE 8069

# Set the entrypoint for the container
ENTRYPOINT ["/entrypoint.sh"]
