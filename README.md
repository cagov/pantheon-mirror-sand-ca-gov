# Getting started:

Clone from pantheon.

`git clone ssh://codeserver.dev.ceac7b01-5bdb-4089-ac7b-302c5c3c1512@codeserver.dev.ceac7b01-5bdb-4089-ac7b-302c5c3c1512.drush.in:2222/~/repository.git sand-ca-gov`

Add Github as second remote.

`git remote set-url --add origin https://github.com/cagov/pantheon-mirror-sand-ca-gov.git`

Set upstream.

`git push --set-upstream origin master`

Check for both remotes.

`git remote -v`

Result should be:

```
origin  ssh://codeserver.dev.ceac7b01-5bdb-4089-ac7b-302c5c3c1512@codeserver.dev.ceac7b01-5bdb-4089-ac7b-302c5c3c1512.drush.in:2222/~/repository.git (fetch)
origin  ssh://codeserver.dev.ceac7b01-5bdb-4089-ac7b-302c5c3c1512@codeserver.dev.ceac7b01-5bdb-4089-ac7b-302c5c3c1512.drush.in:2222/~/repository.git (push)
origin  https://github.com/cagov/pantheon-mirror-sand-ca-gov.git (push)
```