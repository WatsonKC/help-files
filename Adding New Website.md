# Steps to add a new site to this web server
## Setup the Git Repository
### Initialize a New `bare` Repository
1. Access the `git` user on the server using the following command: `sudo -u git -i`.
2. Make a new directory for your repository.
    1. Ex: `mkdir new-repo.git`
    2. As a best practice, ensure the `.git` extension is used at the end of the folder name.
3. Access the newly created folder: `cd new-repo.git`.
4. Create a new `bare` Git repository using the following command: `git init --bare`.
### Create the `post-receive` hook
1. Create a `post-receive` hook in the following folder: `new-repo/hooks/`.
2. The following sample file can be copied and modified to suit your needs.
    ```
    echo 'post-receive script: TRIGGERED'
    cd /var/www/media-library

    echo 'post-receive script: checking out repo'
    git --git-dir=/home/git/media-library.git --work-tree=/var/www/media-library checkout master -f
    
    echo 'post-receive script: installing npm'
    npm ci \
    && echo 'post-receive script: building app' \
    && npm run build \
    && echo 'post-receive script: → COMPLETE' \
    && (pm2 delete 'media-library' || true) \
    && pm2 start npm --name 'media-library' -- start \
    && echo 'post receive script: media-library start successfully with pm2'
    ```
3. The following areas of the file should be modified:
    | Text line | Description |
    | ---- | ----------- |
    | --git-dir=`/home/git/media-library.git` | Replace with the location of the `bare` repository you created previously. |
    | --work-tree=`var/www/media-library` | Replace with the location of where your pushed code should live. |
    | checkout `master` | Replace with the name of the branch. |
    | pm2 delete '`media-library`' | Replace with the name of the application. |
    | pm2 start npm --name '`media-library`' | Replace with the name of the application. |
    |'post receive script: `media-library` | Replace with the name of the application. |
4. Ensure the permissions of the file match the following:
    - file permissions: `rwxr-xr-x` (755)
    - owner: `git`
    - group: `git`
5. Restart Nginx to apply changes:
    - `sudo systemctl restart nginx`
## Ensure the new web site is added to Nginx as an available site.
1. Available sites can be located here: `/etc/nginx/sites-available`.
2. You can copy an existing site to create your new configuration.
    1. Ensure the permissions of all sites are consistent.
    2. At the time of writing `root` is the owner and group of all sites.
3. Updates should be made to the following fields:
    | Field | Description of Changes |
    | ------ | ----------------- |
    | listen | Specifies the port used for the server. |
    | root | Specifies the location of the website code's root directory. |
    | index | Most sites include `.html` and `.htm` files. Add additional extensions as needed. |
    | server_name | Specifies the subdomain and domain of the website. |
4. Once the site has been configured a symbolic link (symlink) needs to be added to the enabled sites folder.
    1. Enabled sites can be located here: `/etc/nginx/sites-enabled`.
    2. A symlink can be created with the following code: `ln -s [source] [destination]`. Example:
        > `[source]` is replaced with `/etc/nginx/sites-available/kcmozou.com`.
        > `destination` is replaced with `/etc/nginx/sites-enabled/kcmozou.com`.
## Add Subdomain to Cloudflare
1. A new DNS record needs to be added to [Cloudflare](https://dash.cloudflare.com/b686410026ae13ac7abe3d38a70af4aa/kcmozou.com/dns/records).
2. A `CNAME` record needs to be created, pointing the `subdomain` to the existing server.
    | Field | Description |
    | ------------ | ----------- |
    | Type | CNAME |
    | Name | Use the `subdomain` associated with the new website. |
    | Target | kcmozou.com |
    | Proxy Status | Off |
    | TTL | Auto |