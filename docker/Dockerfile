FROM odoo:16

USER root

# Copy configuration files and scripts
COPY odoo.conf /etc/odoo/
COPY . update_module_list.py

# Ensure the script is executable
RUN chmod +x update_module_list.py