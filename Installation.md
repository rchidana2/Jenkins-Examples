# Jenkins & Compatible JDK Installation on Ubuntu 24.04

## 1. Update Ubuntu

```bash
sudo apt update -y
```

## 2. Install Prerequisites

```bash
sudo apt install -y \
    ca-certificates \
    curl \
    wget \
    gnupg \
    fontconfig
```

## 3. Install Java 21

Java 21 is recommended for Jenkins. Install Java 21 and verify the installation:

```bash
sudo apt install -y openjdk-21-jdk

java --version
```

## 4. Create the Keyring Directory

```bash
sudo mkdir -p /etc/apt/keyrings
```

## 5. Install the Latest Jenkins Signing Key

```bash
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
    https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
```

## 6. Verify the Jenkins Signing Key Fingerprint

```bash
gpg --show-keys /etc/apt/keyrings/jenkins-keyring.asc
```

## 7. Add the Jenkins Repository

```bash
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | \
    sudo tee /etc/apt/sources.list.d/jenkins.list
```

## 8. Verify the Jenkins Repository

```bash
cat /etc/apt/sources.list.d/jenkins.list
```

## 9. Update Package Metadata

```bash
sudo apt update
```

## 10. Install Jenkins

```bash
sudo apt install -y jenkins
```

## 11. Enable & Start Jenkins Service

Enable Jenkins to start automatically at boot:

```bash
sudo systemctl enable jenkins
```

Start the Jenkins service:

```bash
sudo systemctl start jenkins
```

## 12. Verify Jenkins Service Status

```bash
sudo systemctl status jenkins
```

> **Note:** Once Jenkins is installed and running, it needs to be configured through the web interface.

---

# Jenkins Initial Configuration

## 13. Open Jenkins in a Browser

Once Jenkins is up and running, open:

```text
http://localhost:8080
```

For a remote server, use:

```text
http://<YOUR_SERVER_IP>:8080
```

## 14. Retrieve the Initial Admin Password

Run:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

The command will display a password similar to:

```text
c9be7437ceaf43..ada4rd...da
```

Copy and paste this password into the Jenkins setup screen.

## 15. Install Suggested Plugins

Click:

**Install Suggested Plugins**

Wait until all the recommended plugins have been installed.

## 16. Create the First Admin User

Create the first Jenkins administrator account using your preferred username and password.

## 17. Save & Continue

Click:

**Save & Continue**

Then click:

**Save & Finish**

## 18. Jenkins is Ready!

🎉 **Congratulations! Your Jenkins installation is complete and Jenkins is ready to use.**
