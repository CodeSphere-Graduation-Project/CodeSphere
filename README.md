# CodeSphere
desc 

---
# Local Development

## Dependencies

Install these dependencies if you don't already have them:

1. Git
2. Docker for Desktop
3. Node.js v20
4. Yarn
5. mkcert

## Dependencies Installation Process

### 1. Git
To check if Git is installed:
```shell
git --version
```
If not, install it using the following commands:

#### **Linux (Ubuntu/Debian)**
```shell
sudo apt install git
```

#### **Windows**
```powershell
winget install --id Git.Git -e --source winget
```

### 2. Docker for Desktop
Download and install Docker from the official website:
[Docker Desktop](https://www.docker.com/products/docker-desktop/)

### 3. Node.js v20
Check if Node.js is installed:
```shell
node -v
```
If not, download and install version **v20.18.3 (LTS)** from:
[Node.js Download](https://nodejs.org/en/download)

Choose your operating system and follow the installation instructions.

### 4. Yarn
Check if Yarn is installed:
```shell
yarn -v
```
If not, install it with:
```shell
npm install --global yarn
```

### 5. mkcert
Check if mkcert is installed:
```shell
mkcert -version
```
If not, install it using the following methods:

#### **Windows**
##### **1. Install via Chocolatey (Recommended)**
```powershell
choco install mkcert -y
```
##### **2. Install via Scoop**
```powershell
scoop install mkcert
```

#### **Linux**
##### **1. Install via Package Manager**
**Debian/Ubuntu:**
```shell
sudo apt update && sudo apt install -y libnss3-tools
curl -L https://github.com/FiloSottile/mkcert/releases/latest/download/mkcert-linux-amd64 -o mkcert
chmod +x mkcert
sudo mv mkcert /usr/local/bin/
```

---

## Downloading the Source Code
Clone the repository with:
```shell
git clone git@github.com:outline/outline
```

---

## Configuration

### Environment Variables (.env)
Copy the `.env.sample` file to `.env` and update the following variables:
```text
NODE_ENV=development
```

Generate a `SECRET_KEY` and `UTILS_SECRET` using:
```shell
openssl rand -hex 32
```
Example:
```text
SECRET_KEY=83e9a5f23d24494f02ec2f9dec18062586b0db6d0439d963de76b56ab3fa9570
UTILS_SECRET=3dbab21236561c47a1a9b0320a55d279797f9a55d766d4925fe156427e1d0f81
```
Update the `URL` variable:
```text
URL=https://app.outline.dev
```

You must configure at least one [authentication provider](/s/hosting/doc/authentication-7ViKRmRY5o) and set up the **Redirect URLs**.
Example for Slack authentication:
```text
https://app.outline.dev/auth/slack.callback
https://local.outline.dev:3000/auth/slack.callback
```

### Hosts Configuration
Add the following entries to your `/etc/hosts` file to allow local development domains to load:

#### **Linux/macOS**
```text
127.0.0.1     app.outline.dev
127.0.0.1     wiki.outline.dev
127.0.0.1     local.outline.dev
```

#### **Windows**
1. Open Notepad as Administrator.
2. Click **File** > **Open** and navigate to:
   ```
   C:\Windows\System32\drivers\etc\hosts
   ```
3. Select "All Files" to view the `hosts` file.
4. Add the following lines at the end:
   ```text
   127.0.0.1     app.outline.dev
   127.0.0.1     wiki.outline.dev
   127.0.0.1     local.outline.dev
   ```
5. Save the file and restart your terminal.

---

## Running the Application
To start the development environment, run:
```shell
make up
```
