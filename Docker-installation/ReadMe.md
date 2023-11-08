Installing Docker on Ubuntu is a straightforward process that can be done through the terminal. Here's a step-by-step guide to get Docker installed on your Ubuntu system:
### Step 1: Update Software Repositories
Open a terminal and run the following command to ensure your package lists are up to date:
```sh
sudo apt update -y
```
### Step 2: Install Prerequisite Packages
Before you install Docker, you'll want to ensure that your system has the `apt-transport-https`, `ca-certificates`, `curl`, and `software-properties-common` packages installed. These allow you to add external HTTPS sources to your package manager.
```sh
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
```
### Step 3: Add Docker's GPG Key
Docker signs its repositories with a GPG key to ensure the integrity of the downloaded packages. Add the GPG key for Docker's official repository to your system:
```sh
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
### Step 4: Add Docker Repository to APT Sources
Now, add the Docker repository to APT sources:
```sh
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```
This command will add the repository and also update your package list after adding it.
### Step 5: Install Docker
First, refresh your package list due to the addition of the new repository:
```sh
sudo apt update
```
Next, install Docker. The Docker package available in the official Ubuntu 16.04 repository may not be the latest version. To ensure you get the latest version, install Docker from the Docker repository you just added:
```sh
sudo apt install docker-ce -y
```
### Step 6: Verify Docker is Installed
To verify that Docker has been installed and the service is running, enter:
```sh
sudo systemctl status docker
```
### Step 7: Run Docker Without `sudo` (Optional)
By default, running the `docker` command requires administrator privileges (i.e., prefixing with `sudo`). To run Docker commands as your non-root user, you need to add your user to the `docker` group:
```sh
sudo usermod -aG docker ${USER}
```
To apply the new group membership, you can log out of the server and back in, or you can type the following:
```sh
su - ${USER}
```
You will be prompted to enter your user's password to continue.
### Confirm that your user is now added to the Docker group by running:
```sh
id -nG
```
### Step 8: Testing Docker
To ensure that Docker was installed correctly and is functioning, run the hello-world image:
```sh
docker run hello-world
```
This command downloads a test image and runs it in a container. When the container runs, it prints an informational message and exits.
Docker should now be installed and ready to use on your Ubuntu system.