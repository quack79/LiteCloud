# LiteCloud

LiteCloud is a collection of shell scripts for simple deployment of a LEMP stack (Linux, Nginx, MariaDB and PHP 8.4) for Ubuntu.

### The following are going to be installed:

-   Nginx
-   MariaDB (or MySQL)
-   PHP-FPM + commonly used PHP modules
-   Let's Encrypt SSL
-   Postfix

### Requirements

-   Fresh install of Ubuntu 24.04 (at least)

### Quick Install (Git)

    # Update, upgrade and install git
    sudo apt update
    sudo apt upgrade
    sudo apt install git

    # Clone LiteCloud repo
    git clone https://github.com/quack79/LiteCloud.git ; cd LiteCloud ; chmod 700 *.sh ; chmod 700 options.conf

    # Edit options to enter server IP, MariaDB/MySQL password etc.
    nano options.conf

    # Install LEMP stack.
    ./install.sh

### DONE!

<details>

<summary>Additional commands</summary>

#### Add a new Linux user, and add to sudoer (if root was disabled in options).

    # To add user
    adduser johnsmith

    # To add user to sudoer
    usermod -aG sudo johnsmith

#### Add domain to the user

    # Add domains to the user
    ./domain.sh add johnsmith yourdomain.com
    ./domain.sh add johnsmith subdomain.yourdomain.com

    # Add SSL certificates using Let's Encrypt
    ./domain.sh ssl johnsmith yourdomain.com
    ./domain.sh ssl johnsmith subdomain.yourdomain.com

    # Install Adminer or phpMyAdmin
    ./setup.sh dbgui

    # Enable/disable public viewing of Adminer/phpMyAdmin
    ./domain.sh dbgui on
    ./domain.sh dbgui off

#### Database and database user management

    # Create and drop database
    ./database.sh add db - Create new database
    ./database.sh rem db - Destroy a database (cannot be undone)

    # Create and remove user
    ./database.sh add user - Create new user
    ./database.sh add super_user - Create new SUPER user
    ./database.sh rem user - Remove a user (cannot be undone)

</details>

TODO:

Install Wordpress automatically

