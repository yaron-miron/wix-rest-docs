SortOrder: 1
# Use cases

## Backups

### Take a backup manually

Submit a `takeBackup` request. The process of backing up your live site data will be started in the background.

### Check if your backup has been successfully created

Send `listBackups` request. In response, validate if relevant backup has `READY` status which indicates it can be used.

### Find most recent backup of instance data and use it to restore

Find the ID of backup you want use with `listBackups` request with  `status` field `["READY"]`. This will list your
ready backups from newest to oldest. Send `restoreBackup` request using the ID of your selected backup.

### Check if your data restoration has successfully completed

Send `listRestorations` request. Restoration has finished successfully if its status is `COMPLETED`.

### Remove backups you no longer need

Use `listBackups` to check existing backups. Send a `deleteBackup` request with a backup ID
that you want to remove.
