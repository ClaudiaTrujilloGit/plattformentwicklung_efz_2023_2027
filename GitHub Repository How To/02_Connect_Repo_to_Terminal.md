# Description
In this example I'll connect a GitHub repository to my WSL terminal using an SSH-Key.

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

## Connect repository to the terminal

**Install Git**
```
sudo apt update && sudo apt upgrade
sudo apt install git
git --version
```

**Create a folder for the repo**
```
cd /path/createdFolder
```

**Initialize Git and configure Git**
```
git init
git config --global user.name "github-username"
git config --global user.email "email-address-used-for-the-github-account"
```

**Connect to the repository**
```
git remote add origin https://github.com/[github-username]/[repository-name].git
git remote -v

(output)
origin  git@github.com:[github-username]/[repository-name].git (fetch)
origin  git@github.com:[github-username]/[repository-name].git (push)
```

**Set access token**
```
git remote set-url origin git@github.com:[github-username]/[repository-name].git
```

**Bring remote commits into your local branch**
```
git fetch origin
git switch main
git pull origin
```

<br>

Now it's done.

## Try your first commit
1. touch text.txt
2. git add .
3. git commit -m "test commit"
4. git push origin