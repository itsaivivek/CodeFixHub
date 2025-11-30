# How to install Postman on Ubuntu (or Ubuntu Based Distribution)

Postman may be installed in a variety of methods on Ubuntu (or its derivatives). Let's take a look at each one individually.

## Using Official Postman tar.gz file

_**Note :** Postman installed using snap package manager doesn't run then this method works in all cases._

- **Step 1: Download archive file**:

    Download the tar.gz file from this link https://dl.pstmn.io/download/latest/linux or go the website to download it.
- **Step 2: Extract files from archive**:
    Open terminal and go to Download folder where the tar.gz file is downloaded using this command:
    ```
    cd Downloads
    ```
    See the list of files using `ls` command. There will be like this `postman-linux-x64.tar`

    Paste this tar command to extract files

    ```
    tar -xzf postman-linux-x64.tar
    ```

    If any version is installed before, remove it.

    ```
    sudo rm -rf /opt/Postman
    ```

- **Step 3: Move Postman**:

    ```
    sudo mv Postman /opt/Postman
    ```

- **Step 4: Create a symbolic link**:

    ```
    sudo ln -s /opt/Postman/Postman /usr/bin/postman
    ```
- **Step 5: Create a desktop file**:

    ```
    cat > ~/.local/share/applications/postman.desktop <<EOL
    [Desktop Entry]
    Encoding=UTF-8
    Name=Postman
    Exec=postman
    # Before v6.1.2
    # Icon=/opt/Postman/resources/app/assets/icon.png
    Icon=/opt/Postman/app/resources/app/assets/icon.png
    Terminal=false
    Type=Application
    Categories=Development;
    EOL
    ```

## Using Snapcraft

- **Step 1: Install 'snapd' on Ubuntu**

    We may get Postman from the snapcraft shop using the 'snapd' tool, but first we must ensure that the snapd program is installed on Ubuntu; if it is not, run the command below to install it:

    ```
    sudo apt install snapd
    ```
 
- **Step 2: Install Postman via Snapcraft**

    Then, using the snap package manager, download and install Postman:

    ```
    sudo snap install postman
    ```
 
## Method 2: Using Flathub

- **Step 1: Install 'flatpak' on Ubuntu**

    Flathub, like snapcraft, is a Linux application store, therefore we can use the flatpak program to download and install postman from there. We'll use the apt package manager to install the flatpak utility.

    ```
    sudo apt install flatpak
    ```
    
- **Step 2: Install Postman from Flathub**

    Using the flatpak program, download and install the postman package from flathub.

    ```
    flatpak install flathub com.getpostman.Postman
    ```


Step 3: Launch Postman
To launch Postman, navigate to the Application menu's search field, type "postman," and then click on the Postman application icon:

Now we successfully install Postman on our Ubuntu Operating System.


