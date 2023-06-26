# simple-instance-template

## Installation

```bash
# install NVM
curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash
. ~/.bashrc
# use NVM to install and activate node 16
nvm install v16
# either install yarn globally with "corepack enable"
# as per https://yarnpkg.com/getting-started/install
# or set a bash alias:
alias yarn=.yarn/releases/yarn-3.2.2.cjs
# checkout repository
git clone git@github.com:tiddlybase/simple-instance-template.git tiddlybase-simple-instance-template
cd tiddlybase-simple-instance-template/
# install dependencies
yarn
# login to firebase
yarn firebase login
# Visit printed URL to log in with oauth
# Set active project
yarn firebase projects:list
yarn firebase use --add tiddlybase-simple-instance
# Create web app within firebase project
yarn firebase apps:create web simple
# Enable firestore in the Firestore dashboard at
# https://console.firebase.google.com/project/tiddlybase-simple-instance/firestore
# Enable hosting
# Enable Google auth provider in Authentication
# Generate tiddlybase-config.json
yarn tiddlybase generate:tiddlybase-config.json simple
# Generate firebase.json
yarn tiddlybase generate:firebase.json
# Generate firestore rules
yarn tiddlybase generate:firestore.rules
# Generate HTML for parent frame (outer.html)
yarn tiddlybase generate:outer.html
# Add symlink for tiddlybase_public dir
pushd simple/public/
ln -s ../../node_modules/@tiddlybase/tiddlybase-public/tiddlybase_public tiddlybase_public
popd
# list firebase hosting sites
yarn firebase hosting:sites:list
# Set site-id in tiddlybase-config.json
# deploy
yarn run deploy
# Download service account key
# Move service account key json into etc folder
mv ~/Sync/tiddlybase-simple-instance-firebase-adminsdk-789py-7e806fa0a7.json etc/service-account-key.json
# create users and authorize access to wiki
yarn tiddlybase adduser tiddlybase.test@gmail.com
yarn tiddlybase setcollectionrole tiddlybase.test@gmail.com 'user:$USERID' editor
yarn tiddlybase setcollectionrole tiddlybase.test@gmail.com 'shared' editor
# note: you will ONLY be able to log in from the URL set in tiddlybase-config.json under firebase.clientConfig.authDomain. In this case,
# https://tiddlybase-simple-instance.firebaseapp.com/
```
