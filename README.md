# OpenShift WordPress Import Export

Allows OpenShift WordPress Quick Starter Users a flexible way to import and export their SQL database, ~/data/plugins and ~/data/uploads.

This is exceptionally useful when migrating between OpenShift Application installs and keeping full backups of all dynamic data in the OpenShift WordPress Quick Starter Application.

*WARNING:* This script is **ONLY DESIGNED** for use with the OpenShift WordPress Quick Starter.

*REFERENCE:* [OpenShift WordPress Quick Starter](https://github.com/openshift/wordpress-example)

## Installation

1. Copy the folder `+BACKUP_WP+` into the base folder of your WordPress Quick Starter OpenShift Application.
	![alt text](http://www.adanrehtla.com/assets/github/OpenShift-WordPress-Import-Export/OpenShift-WordPress-Quick-Starter-Backup-Import-Export-Script-01.png "Files copied into the base Wordpress Quick Starter Repo")
2. *OPTIONAL:* Set the files `wp_import` and `wp_export` to `+x` executable via git.
3. Commit the files to the server.

## Usage

### TO BACKUP

1. SSH into the OpenShift Application.
2. `cd app-root/repo/+BACKUP_WP+`.
3. *OPTIONAL:* `chmod +x wp_*` Make the files executable, if not already done so.
4. `./wp_export` will begin the export process.
	![alt text](http://www.adanrehtla.com/assets/github/OpenShift-WordPress-Import-Export/OpenShift-WordPress-Quick-Starter-Backup-Import-Export-Script-02.png "Starting the Export process")
5. Use SFTP to download the 2 tar.gz files created in the `+BACKUP_WP+` folder, one will contain the DATA and the other will contain the SQL.
	![alt text](http://www.adanrehtla.com/assets/github/OpenShift-WordPress-Import-Export/OpenShift-WordPress-Quick-Starter-Backup-Import-Export-Script-03.png "The 2 latest backup tar.gz files")
6. When this script is run multiple times, the latest backup tar.gz files will be stored in `+BACKUP_WP+/+BACKUP+`.

### TO RESTORE

**IMPORTANT:** There should only be **1 SET** of `*.LATEST.*.tar.gz` files in the `+WP_BACKUP+` folder during the import process. A set of backup files includes a single `*.LATEST.DATA.tar.gz` and a single `*.LATEST.SQL.tar.gz` both stored in the `+WP_BACKUP+` folder.

1. Delete/Recreate your OpenShift WordPress Quick Starter.
2. Copy your existing repo files into the freshly pulled repo folder.
3. Remeber to install the `+BACKUP_WP+` folder.
	![alt text](http://www.adanrehtla.com/assets/github/OpenShift-WordPress-Import-Export/OpenShift-WordPress-Quick-Starter-Backup-Import-Export-Script-01.png "Files copied into the base Wordpress Quick Starter Repo")
4. Remeber to include the latest set backup files inside the `+BACKUP_WP+` folder.
	![alt text](http://www.adanrehtla.com/assets/github/OpenShift-WordPress-Import-Export/OpenShift-WordPress-Quick-Starter-Backup-Import-Export-Script-03.png "The 2 latest backup tar.gz files")
5. Commit the changes and oush them to the server.
6. SSH into the OpenShift Application.
7. `cd app-root/repo/+BACKUP_WP+`.
8. *OPTIONAL:* `chmod +x wp_*` Make the files executable, if not already done so.
9. `./wp_import` will begin the import process.

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## History

v1.0 - First version with command line usage

## Credits

Developer: Adan Rehtla

## License

GNU GPL v2.0
