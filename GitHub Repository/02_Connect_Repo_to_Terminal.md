# Description
In this example I'll connect a GitHub repository to my WSL terminal using an SSH-Key.


# Connect repository to the terminal

## Previous Steps
**Create an SSH-Key and add it to the repo**
```
ssh-keygen -t ed25519 -C "email-address-used-for-the-github-account"
```

This generates two keys: 
- id_ed25519.pub (public key)
- id_ed25519 (private key)

then display the public key using cat and copy it
```
cat /home/[username]/.ssh/id_ed25519.pub
```

add the key into the repository:
- account settings > access: SSH and GPG keys > new SSH Key
- Enter a titel and then enter the public key you just created and copied

**Stablish SSH Connection to GitHub**
```
ssh -T git@github.com
```

**Create a local folder for your repo**
```
mkdir /path/[folder-name]
```

## Procedure

**Install Git**
```
sudo apt update && sudo apt upgrade
sudo apt install git
git --version
```

**Initialize Git**
```
cd /path/createdFolder
git init
```

**Configure Git**
```
git config user.name "github-username"
git config user.email "email-address-used-for-the-github-account"
```

**Add repository**
```
git remote add origin "https://github.com/[github-username]/[repository-name].git"
```

**Clone repository**
```
git clone https://github.com/[github-username]/[repository-name].git
```

**Fetch branches**
```
git fetch -all
```

## Try your first commit
1. Create a file -> `touch text.txt`
2. Stage changes -> `git add -u`.
3. Commit changes ->`git commit -m "message"`.  
4. Push to remote ->`git push origin <branch>`.  
5. Sync with remote
    - Update info: `git fetch`  
    - Reset local to match remote: `git reset --hard origin/[default-branch]`  
6. View commits ->`git log`, `git show`, `git diff`.  

```
```
