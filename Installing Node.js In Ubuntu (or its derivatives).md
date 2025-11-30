## Installing Node.js in Ubuntu(or Ubuntu based distro)

There are several methods to install Node.js on Ubuntu (or its derivatives). The easiest and most common methods involve using the system's package manager (apt) or the Node Version Manager (NVM).

- **Method 1: Using apt (System Package Manager)**:

    This method installs Node.js from the official Ubuntu repositories. Update your package list:

    ```
    sudo apt update
    ```
    Install Node.js and npm:

    ```
    sudo apt install nodejs npm
    ```
    Verify the installation:

    ```
    node -v
    npm -v
    ```

    These commands will display the installed versions of Node.js and npm, confirming the installation.

- **Method 2: Using Node Version Manager (NVM)**:

    NVM allows you to install and manage multiple Node.js versions on your system, which is beneficial for development where different projects may require different Node.js versions. Install curl (if not already installed).

    ```
    sudo apt install curl
    ``` 

    Paste the whole command at once into the terminal. This will automatically install nodejs using nvm

    ```
    # Download and install nvm:
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash

    # in lieu of restarting the shell
    \. "$HOME/.nvm/nvm.sh"

    # Download and install Node.js:
    nvm install 24

    # Verify the Node.js version:
    node -v # Should print "v24.11.1".

    # Verify npm version:
    npm -v # Should print "11.6.2".
    ```
    _**Note** : You should visit https://nodejs.org/en/download to download latest version of the nodejs. There will be same command like above to install node.js_
