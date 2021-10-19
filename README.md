# ODI Publishing 11ty Sandbox - Pantheon

Pantheon WordPress code for [dev-sand-ca-gov.pantheonsite.io](https://dev-sand-ca-gov.pantheonsite.io/)

[dev-sand-ca-gov.pantheonsite.io](https://dev-sand-ca-gov.pantheonsite.io/) serves as an endpoint for [odi-publishing-11ty-sandbox](https://github.com/cagov/odi-publishing-11ty-sandbox/)


## Steps to reproduce

1. Clone from pantheon.

    `git clone ssh://codeserver.dev.ceac7b01-5bdb-4089-ac7b-302c5c3c1512@codeserver.dev.ceac7b01-5bdb-4089-ac7b-302c5c3c1512.drush.in:2222/~/repository.git sand-ca-gov`

2. Ensure local code pushes to Pantheon and Github.
    
    - Add Github as second remote.

        `git remote set-url --add origin https://github.com/cagov/pantheon-mirror-sand-ca-gov.git`

    -  Set upstream.

        `git push --set-upstream origin master`

    - Check for both remotes.

        `git remote -v`

        Result:

        ```
origin  ssh://codeserver.dev.ceac7b01-5bdb-4089-ac7b-302c5c3c1512@codeserver.dev.ceac7b01-5bdb-4089-ac7b-302c5c3c1512.drush.in:2222/~/repository.git (fetch)
origin  ssh://codeserver.dev.ceac7b01-5bdb-4089-ac7b-302c5c3c1512@codeserver.dev.ceac7b01-5bdb-4089-ac7b-302c5c3c1512.drush.in:2222/~/repository.git (push)
origin  https://github.com/cagov/pantheon-mirror-sand-ca-gov.git (push)
        ```

4. Import database and files from drought and merge code from drought. 

@todo create clean installation profile instead.

3. Make databse changes

    - Connect to pantheon database (see Connection info on Pantheon dashboard)

    - Change wp_options.siteurl and wp_options.home to http://dev-sand-ca-gov.pantheonsite.io/

    - Change wp_options.blogname and wp_options.blogdescription

    - Change Admin password
        
        `terminus wp sand-ca-gov.dev -- user update Admin --user_pass={{soemthing secure}}`

    - Login 

    - Clean db:
    
    @todo See if we can do this in the database or with a script.


        - Delete extra users and any content.

        - Turn off [notifications](https://dev-sand-ca-gov.pantheonsite.io/wp-admin/edit.php?post_type=notification)

        - Delete the url field from each notification. 
            
            * Notifications > {a notification} > Edit 
            
            * Remove URL field
    
            * Save

        - Delete posts, pages, and media. 


# AWS url 

See [docs](https://github.com/cagov/odi-engineering/wiki/Setting-up-a-new-headless-site-instance#set-up-a-new-aws-bucket-and-publish-the-headless-instance-to-aws) for setup

http://development.sand.ca.gov.s3-website-us-west-1.amazonaws.com


# Configuration for [odi-publishing-11ty-sandbox](https://github.com/cagov/odi-publishing-11ty-sandbox/wordpress/config/wordpress-to-github.development.json)

```
 "data": {
    "wordpress_source_url": "https://dev-sand-ca-gov.pantheonsite.io/",
    "github_targets": [
      {
        "outputBranch": "development",
        "disabled": false,
        "PostPath": "wordpress/posts",
        "PagePath": "wordpress/pages",
        "MediaPath": "wordpress/media",
        "GeneralFilePath": "wordpress/general/general.json",
        "ExcludeProperties": [
          "content",
          "_links"
        ]
      }
    ]
  }
  ```

# Configuration for [wordpress-to-github endpoints.json](https://github.com/cagov/wordpress-to-github/blob/main/WordpressSync/endpoints.json)
```
"projects": [
      {
        "name": "development.sand",
        "enabled": false,
        "enabledLocal": true,
        "GitHubTarget": {
          "Owner": "cagov",
          "Repo": "odi-publishing-11ty-sandbox",
          "Branch": "development",
          "ConfigPath": "wordpress/config/wordpress-to-github.development.json"
        }
      }
    ]
    ```