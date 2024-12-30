# Use the official Odoo image as the base
FROM odoo:16

# Copy your custom addons into the container
COPY ../addons /mnt/extra-addons

# Copy your Odoo configuration file into the container
# COPY ./etc/odoo.conf /etc/odoo/
COPY odoo.conf /etc/odoo/
# Set the environment variable for the Odoo config file
ENV ODOO_CONF=/etc/odoo/odoo.conf

# Expose the port Odoo will run on
EXPOSE 8069

# Set the entrypoint for the container
ENTRYPOINT ["/entrypoint.sh"]
