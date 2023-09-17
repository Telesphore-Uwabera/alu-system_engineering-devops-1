# Project: Nginx Server Configuration and Custom 404 Page

This project consists of a series of Bash scripts and web files to configure an Nginx server, perform specific tasks, and create a custom 404 error page. The scripts are designed to automate the installation of Nginx, set up various configurations, and create a visually appealing 404 error page.

## Scripts Overview

### `transfer_file.sh`
This script transfers a file from a client to a server using SCP. It takes the following arguments:
- `PATH_TO_FILE`: The path to the file you want to transfer.
- `IP`: The server's IP address.
- `USERNAME`: The username for SSH access.
- `PATH_TO_SSH_KEY`: (Optional) The path to the SSH key for authentication.

### `install_nginx.sh`
This script installs Nginx on a remote server and configures it. It performs the following tasks:
- Updates the package repository.
- Installs Nginx.
- Creates an HTML file at `/var/www/html/index.html` with the text "Holberton School."
- Starts the Nginx service.

### `configure_redirect.sh`
This script configures the Nginx server to redirect requests to `/redirect_me` to a specific URL (in this case, a YouTube video). It does the following:
- Updates the package repository.
- Installs Nginx.
- Allows HTTP traffic through the firewall.
- Modifies the default Nginx configuration to perform the redirection.
- Starts the Nginx service.

### `custom_404.sh`
This script configures the Nginx server to have a custom 404 error page with the text "Ceci n'est pas une page." It performs the following steps:
- Updates the package repository.
- Installs Nginx.
- Creates an HTML file at `/var/www/html/error404.html` with the custom 404 message.
- Modifies the default Nginx configuration to use this custom error page.
- Restarts the Nginx service.

## Web Files

### `5-design_a_beautiful_404_page.css`
This CSS file defines the styling for the custom 404 error page. It creates a visually appealing and responsive design for the error page.

### `404-Isaiah.html`
This HTML file represents the custom 404 error page. It includes the text "Ceci n'est pas une page" and provides a user-friendly error message along with a link to return to the home page.

## Usage

To use these scripts, follow these steps:

1. Make sure you have SSH access to the server where you want to run the scripts.
2. Copy the scripts and web files to the server.
3. Ensure that the scripts have execute permissions using `chmod +x script_name.sh`.
4. Execute the scripts with the appropriate arguments as described in their respective sections.

## Important Notes

- Make sure to handle SSH key management securely when using the `transfer_file.sh` script with a key.
- Ensure that you have appropriate permissions to run administrative commands on the server when using the other scripts.
- Customize the scripts and web files to suit your specific requirements, such as server IP, paths, and error page content.
