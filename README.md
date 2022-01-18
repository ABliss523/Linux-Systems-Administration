# Linux-Systems-Administration
### Scenario 

You are tasked with preparing a new server.

### Lab Environment
Firstly, log into your local virtual machine. 

Secondly, open the Terminal within your Ubuntu VM. 

#### Step 1: Ensure Permissions on Sensitive Files

Within the `/etc/` directory, where system configuration files exist, inspect the file permissions of each of the files below.
If they do not match the descriptions, please update the permissions.

  1. Permissions on `/etc/shadow` should allow only `root` read and write access.

  2. Permissions on `/etc/gshadow` should allow only `root` read and write access.

  3. Permissions on `/etc/group` should allow `root` read and `write` access, and allow everyone else `read` access only.

  4. Permissions on `/etc/passwd` should allow `root` read and `write` access, and allow everyone else `read` access only.

The following is the commands used to set the requested permissions above.
1. Permissions for `/etc/shadow` should be `600` (`rw` for root only):

    - **Command**: `ls -l /etc/shadow` shows the permissions are set to `640`.
  
   - **Command**: `sudo chmod 600 /etc/shadow`

2. Permissions for `/etc/gshadow` should be `600`` (`rw` for root only):

   - **Command**: `ls -l /etc/gshadow` shows the permissions set to `640`.
  
    - **Command**: `sudo chmod 600 /etc/gshadow`.

3. Permissions for `/etc/group` should be `644` (`rw` for root and `r` for anyone else):

    - **Command**: `ls -l /etc/group` shows that the permissions are already set to `644`.

4. Permissions for `/etc/pssw` should be `644` (`rw` for root and `r` for anyone else):

   - **Command**: `ls -l /etc/passwd` shows that the permissions are already set to `644`.


### Step 2: Create User Accounts
1. Add user accounts for `sam`, `joe`, `amy`, `sara`, and `admin`.

    - **Command**: `sudo useradd sam`

    - **Command**: `sudo useradd joe`

    - **Command**: `sudo useradd amy`

    - **Command**: `sudo useradd sara`

    - **Command**: `sudo useradd admin`


2. Ensure that only the `admin` has general `sudo` access:

    - **Command**: `sudo usermod -G sudo admin`

### Step 3: Create User Group and Collaborative Folder

1. Add an `engineers` group to the system:

    - **Command**: `sudo addgroup engineers`

2. Add users `sam`, `joe`, `amy`, and `sara` to the managed group:

    - **Command**: `sudo usermod -G engineers sam`
    - **Command**: `sudo usermod -G engineers joe`
    - **Command**: `sudo usermod -G engineers amy`
    - **Command**: `sudo usermod -G engineers sara`

3. Create a shared folder for this group at `/home/engineers`:

    - **Command**: `sudo mkdir /home/engineers`

4. Change ownership on the new engineers' shared folder to the `engineers` group:

    - **Command**: `sudo chown :engineers /home/engineers`


### Step 4: Lynis Auditing

1. Install and run Lynis:

    - **Command**: `sudo apt install lynis`

2. Run an audit: 
    - **Command**: `sudo lynis audit system` to run an audit

3. Lynis output on what more could be done to harden the system:

![](https://github.com/ABliss523/Linux-Systems-Administration/blob/main/Lynis%20Output.PNG)

```
