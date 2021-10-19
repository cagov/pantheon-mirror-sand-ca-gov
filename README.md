# What happend/Getting started:

Clone from pantheon.

`git clone ssh://codeserver.dev.ceac7b01-5bdb-4089-ac7b-302c5c3c1512@codeserver.dev.ceac7b01-5bdb-4089-ac7b-302c5c3c1512.drush.in:2222/~/repository.git sand-ca-gov`

Add Github as second remote.

`git remote set-url --add origin https://github.com/cagov/pantheon-mirror-sand-ca-gov.git`

Set upstream.

`git push --set-upstream origin master`

Check for both remotes.

`git remote -v`

Result:

```
origin  ssh://codeserver.dev.ceac7b01-5bdb-4089-ac7b-302c5c3c1512@codeserver.dev.ceac7b01-5bdb-4089-ac7b-302c5c3c1512.drush.in:2222/~/repository.git (fetch)
origin  ssh://codeserver.dev.ceac7b01-5bdb-4089-ac7b-302c5c3c1512@codeserver.dev.ceac7b01-5bdb-4089-ac7b-302c5c3c1512.drush.in:2222/~/repository.git (push)
origin  https://github.com/cagov/pantheon-mirror-sand-ca-gov.git (push)
```

Connect to pantheon database (see Connection info on Pantheon dashboard)

Change wp_options.siteurl and wp_options.home to http://dev-sand-ca-gov.pantheonsite.io/

Change wp_options.blogname and wp_options.blogdescription

Change Admin password
`terminus wp sand-ca-gov.dev -- user update Admin --user_pass={{soemthing secure}}`

Login 

Clean db:
    @todo See if we can do this in the database or with a script.


- Delete extra users and any content.

- Turn off [notifications](https://dev-sand-ca-gov.pantheonsite.io/wp-admin/edit.php?post_type=notification)

- Delete the url field from each notification. 
    * Notifications > {a notification} > Edit 
    * Remove URL field
    * Save

- Delete posts, pages, and media. 