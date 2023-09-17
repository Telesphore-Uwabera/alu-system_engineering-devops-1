
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

# SSH Configuration and Key Generation

This project provides a set of Bash scripts to simplify the process of connecting to a remote server using SSH and setting up SSH key-based authentication. By following these steps, you can enhance the security and convenience of your SSH connections.

## Prerequisites

Before using these scripts, ensure you have the following:

1. A remote server you want to connect to via SSH.
2. Bash shell available on your local machine.
3. Basic knowledge of working with the terminal.

## Usage

### 1. Connect to the Remote Server

Use the following script to establish an SSH connection to the remote server. Replace `35.173.42.252` with your server's IP address and `ubuntu` with the appropriate username if needed.

```bash
#!/usr/bin/env bash
# Connects to a server using SSH
ssh -i ~/.ssh/school ubuntu@35.173.42.252
```

This script uses an SSH key for authentication, providing a secure way to access the server without entering a password each time.

### 2. Generate SSH Key Pair

This step involves generating an SSH key pair (public and private keys) for secure authentication. Run the following script:

```bash
#!/usr/bin/env bash
# Creates a 4096-bit RSA key pair
ssh-keygen -b 4096 -N betty -f school
```

The `-b` option specifies the key size (4096 bits), `-N` sets a passphrase (replace `betty` with your desired passphrase), and `-f` defines the file name for the key pair (in this case, `school`).

### 3. Configure SSH Client

To configure the SSH client for passwordless authentication and specify the identity file, you can use the following scripts. They update the system-wide SSH client configuration file, `/etc/ssh/ssh_config`.

```bash
#!/usr/bin/env bash
# Set up SSH client configuration
include stdlib
file_line { 'Declare identity file':
  path    => '/etc/ssh/ssh_config',
  line    => '    IdentityFile ~/.ssh/school',
  replace => true,
}

file_line { 'Turn off password authentication':
  path    => '/etc/ssh/ssh_config',
  line    => '    PasswordAuthentication no',
  replace => true,
}
```

These scripts add the SSH key file (`~/.ssh/school`) as the identity file and disable password authentication for increased security.

## SSH Configuration

In addition to the scripts, this project includes a sample system-wide SSH configuration file (`/etc/ssh/ssh_config`) with the following settings:

- Hash known hosts for security (`HashKnownHosts yes`).
- Enable GSSAPI-based authentication (`GSSAPIAuthentication yes`).
- Disable GSSAPI credential delegation (`GSSAPIDelegateCredentials no`).
- Specify the identity file (`IdentityFile ~/.ssh/school`).
- Disable password authentication (`PasswordAuthentication no`).

You can customize these settings further to suit your needs.

## Contributing

Feel free to contribute to this project by submitting pull requests or opening issues if you encounter any problems or have suggestions for improvements.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
