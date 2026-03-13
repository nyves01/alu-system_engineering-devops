# SSH

This directory contains scripts and configuration files for SSH connectivity and key management.

## Files

### 0-use_a_private_key
Bash script that connects to a server using SSH with a private key.

**Usage:**
```bash
./0-use_a_private_key <server_ip>
```

**Features:**
- Uses the private key `~/.ssh/school`
- Connects as user `ubuntu`
- Uses only single-character SSH flags (`-i`)

**Example:**
```bash
./0-use_a_private_key 8.8.8.8
```

### 1-create_ssh_key_pair
Bash script that creates an RSA key pair.

**Usage:**
```bash
./1-create_ssh_key_pair
```

**Specifications:**
- Key name: `school`
- Key type: RSA
- Key size: 4096 bits
- Passphrase: `betty`

**Output:**
- `school` (private key)
- `school.pub` (public key)

### 2-ssh_config
SSH client configuration file for passwordless authentication.

**Configuration:**
- Uses private key: `~/.ssh/school`
- Disables password authentication
- Applies to all hosts

**To use this configuration:**
```bash
# Copy to your SSH config location
cp 2-ssh_config ~/.ssh/config

# Or append to existing config
cat 2-ssh_config >> ~/.ssh/config
```

## Requirements

- Bash
- OpenSSH client
- Unix-like operating system (Linux, macOS, WSL)

## Notes

- Ensure scripts have executable permissions: `chmod +x <script_name>`
- Keep private keys secure and never share them
- The SSH config will refuse password authentication for all hosts
