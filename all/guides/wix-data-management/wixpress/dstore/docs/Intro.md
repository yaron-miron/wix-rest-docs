SortOrder: 0
# Wix Data Backup API

With Wix Data Backup API you can create backups of all the live content in your site's collections to protect against
any mistakes or data corruption.

## Automatic backups

All of the content in your site's collections is saved and stored automatically. A save happens every 7 days as long as
there has been a change in any of the content. The content that is saved is the content that is present at the time of
the automatic backup.

## On-demand backups

In addition to automatic backups, you can manually backup your collections at any time. This process does not override
the automatic backup of your collections - it creates an on-demand backup instead.

### Example situation of how this can be used
You're doing a data migration and updating all rows in your site's collections. If something unexpected happens during
the migration, you want to be able to restore your old data. If the weekly automatic back-up is not
recent enough, then you can create an on-demand backup before you start updating your data.

## Backing up your Content

* Backups work only with the Content Manager and live collections in the Content Manager.
* Backups only backup live content, not content in the optional sandbox.
* Backups save and restore content only, not collection structure fields, Schema or named views.
* If there are any content submissions during restoration process, they may be lost.

## Collections

* Backups are of your entire Content Manager, meaning it isn't possible to make backups of individual or groups of
  collections.
* If you create new collections which don’t exist in a backup, and you restore that backup, the new collections' content
  will be erased.

## Limitations

* You can store a maximum of 3 on-demand backups per site.
* If you have 3 existing on-demand backups and create a new one, your oldest on-demand backup will be deleted.