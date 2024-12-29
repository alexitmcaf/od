FROM odoo:16

USER root

# Copy configuration files and scripts
COPY odoo.conf /etc/odoo/
COPY update_module_list.py /scripts/

# Ensure the script is executable
RUN chmod +x /scripts/update_module_list.py