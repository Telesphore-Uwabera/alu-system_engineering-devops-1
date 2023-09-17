
# Nginx Load Balancer Configuration

This project involves configuring an Nginx web server and setting up HAProxy as a load balancer to distribute traffic between two web servers. It also includes custom error pages and a URL redirection configuration.

## Installation

To set up this project on your server, follow these steps:

1. Clone this repository to your server.

2. Execute the `setup.sh` script to configure Nginx and HAProxy.

```bash
./setup.sh
```

The script does the following:

- Removes any existing Nginx installations.
- Installs Nginx.
- Creates custom HTML files for the root and error pages.
- Configures Nginx to serve these HTML files and handle 404 errors.
- Sets up a URL redirection using Nginx.
- Installs HAProxy and configures it as a load balancer.

## Usage

Once the installation is complete, you can access the web servers through the load balancer. The default configuration distributes traffic evenly between two web servers.

- Access the web server through the load balancer:

  ```
  http://your_server_ip/
  ```

- Access the error page:

  ```
  http://your_server_ip/error404.html
  ```

- Perform a URL redirection:

  ```
  http://your_server_ip/redirect_me
  ```

## Configuration

### Nginx Configuration

- The Nginx server listens on port 80.
- The default root directory is `/var/www/html`.
- Custom error pages are configured for 404 errors.
- A URL redirection is set up for the `/redirect_me` path.

### HAProxy Configuration

- HAProxy listens on port 80 and balances traffic between two web servers:
  - `5762-web-01` with IP `52.91.242.136`
  - `5762-web-02` with IP `18.207.144.212`

## Authors

- Telesphore Uwabera

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
```

