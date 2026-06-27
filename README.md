# Secure SSH Key-Based Authentication and Remote Server Management
Step-by-step implementation of secure, SSH key-based authentication on AlmaLinux with client-side integration.
---
## 🚀 Objectives
* Generate a secure 3072-bit RSA cryptographic key pair.
* Transfer and securely map the private key to a local Windows administrator machine.
* Configure a graphical terminal/SFTP tool to authenticate seamlessly via the custom SSH key.
* Establish a successful cryptographic handshake.
---
## 🛠️ Step-by-Step Implementation

### Phase 1: Generating the Cryptographic RSA Key Pair
Initially, logged in as the root administrator on the AlmaLinux host, a secure key generation process was initiated using `ssh-keygen`.

1. Run the `key-gen` tool specifying the `RSA` algorithm.
2. Specify a custom path and filename to save the generated keys.
3. Enter passphrase key. like as ('root')
<img width="767" height="438" alt="Screenshot_1" src="https://github.com/user-attachments/assets/e441d492-5d09-4d7a-b4a7-2519f60dd288" />
</br>
4. Navigate to the hidden `.ssh` directory and verify that both the private and public key files have been created successfully.
</br>
<img width="506" height="87" alt="Screenshot_2" src="https://github.com/user-attachments/assets/51e88690-1bc9-4780-b8f3-ffc0aab6c01b" />
</br>
6. View the raw content of the private key using the `cat` command.
<img width="640" height="662" alt="Screenshot_3" src="https://github.com/user-attachments/assets/87217f1e-adef-4ebd-9ab0-07c22dab9e9d" />
<img width="1362" height="102" alt="Screenshot_4" src="https://github.com/user-attachments/assets/6ebf787b-3851-4317-8255-a2faf2657e99" />

---

### Phase 2: Key Extraction and Windows Configuration

To establish a remote connection from a local workstation, the private cryptographic token must be securely mapped onto the local Windows machine.

1. Open Windows PowerShell as an **Administrator**, navigate to the 'C' drive, and utilize the `nano` editor to recreate the file.
<img width="643" height="232" alt="Screenshot_5" src="https://github.com/user-attachments/assets/de6e88bf-ad4d-42ba-b1ec-d70641cba0b0" />
</br>
2. Paste the exact cryptographic token block into the editor and save it.
<img width="845" height="719" alt="Screenshot_6" src="https://github.com/user-attachments/assets/63f03feb-d09a-4188-9a39-0ba0e9217877" />
</br>
3. Verify that the file `mainul_ssh_key` exists inside `Local Disk (C:)`.
<img width="682" height="362" alt="Screenshot_7" src="https://github.com/user-attachments/assets/2a80408d-5590-45b5-95db-972a6b1ded1b" />
</br>

### Phase 3: SSH Client Integration & Successful Handshake

Using an enterprise SFTP/SSH desktop application.

1. Configure the connection details mapping the username ('root'), password and selecting the custom private key from the folder.
<img width="1097" height="720" alt="Screenshot_8" src="https://github.com/user-attachments/assets/8f87f30b-b96f-4b17-8814-8046357df012" />
<img width="341" height="616" alt="Screenshot_9" src="https://github.com/user-attachments/assets/f3b52cfe-c29e-412a-8b08-234e2c0cb8d9" />
</br>
2. Initialize the connection handshake. Input the key passphrase ('root').
<img width="847" height="623" alt="Screenshot_10" src="https://github.com/user-attachments/assets/49401797-9319-49a0-a2c2-b58c1616c36a" />
</br>
3. Click **"Add and continue"** to permanently append the server to the workstation's known hosts list.
<img width="624" height="540" alt="Screenshot_11" src="https://github.com/user-attachments/assets/d5d1115a-8909-43d9-b504-d845a8769eb4" />
</br>
4. The session authenticates successfully, granting immediate secure terminal access.
<img width="858" height="457" alt="Screenshot_12" src="https://github.com/user-attachments/assets/3b1a8c94-36ed-4e34-9629-11b06d16cdb1" />


## 💻 Tech Stack & Environment Details
* **Operating System:** AlmaLinux (Target Server), Windows 10/11 (Local Workstation)
* **Protocols:** SSHv2, SFTP (Port 22)
* **Cryptography:** RSA 3072-bit Asymmetric Encryption, ECDSA Host Verification
* **Tools Used:** GNU nano, Windows PowerShell, Remote Terminal/SFTP Desktop Client
* **Authentication Method:** Asymmetric Public-Private Key Exchange

