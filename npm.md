# NPM

**Using git repositories**
```bash
npm install --save "git+https://github.com/ajcool2k/jstypes.git#commit"
```

**Install packages globally without sudo**

```bash
# create global npm directory for the user
mkdir ~/.npm-global

# Configure npm to use the path
npm config set prefix '~/.npm-global'

# Open profile to add new directory to PATH
nano ~/.profile

# Add directory to path and save .profile
if [ -d "~/.npm-global/bin" ] ; then
  PATH="$PATH:~/.npm-global/bin"
fi

# Update system variables
source ~/.profile

# install your package globally
npm install -g [package-name]
```

**Install packages from another registry**

```bash
npm install --registry=https://registry.npmjs.org/ [package-name]
```

**Permission for node_modules missing**

```bash
sudo chown -R $(whoami) ~/projects/my-app/node_modules
```



**Linking packages**

```bash
# create source reference
cd ~/projects/my-dependency
npm link

# apply symlink to target
cd ~/projects/my-app/node_modules
npm link my-dependency
```

