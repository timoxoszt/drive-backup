# Drive backup

Laravel-Based Backup Application.

## Introduction
Drive Backup is a backup application intended for VPS or Cloud. A small size and light weight makes Drive Backup a good platform to be hosted even in a small computer such as Raspberry Pi effectively. Built on Laravel 8.75, Drive Backup is easy to install and run even if your hardware is more limited.

## Requirements
- This backup package requires PHP 8.0, with the [ZIP module](https://www.php.net/manual/en/book.zip.php) and <b>Laravel 9.0 or higher</b>. It's not compatible with Windows servers.
- If you are using an older version of Laravel, take a look at one of the previous versions of this package.
- The package needs free disk space where it can create backups. Ensure that you have <b>at least</b> as much free space as the total size of the files you want to backup.
- Make sure `mysqldump` is installed on your system if you want to backup MySQL databases.
- Make sure `pg_dump` is installed on your system if you want to backup PostgreSQL databases.
- Make sure `mongodump` is installed on your system if you want to backup Mongo databases.
## Installation
### Local
```bash
git clone https://github.com/timoxoszt/drive-backup.git
cd drive-backup
cp .env.example .env
composer install
composer update
php artisan key:generate
```
### Create your Google Drive API keys
Detailed information on how to obtain your API ID, secret and refresh token:

-   [Getting your Client ID and Secret](https://github.com/ivanvermeyen/laravel-google-drive-demo/blob/master/README/1-getting-your-dlient-id-and-secret.md)
-   [Getting your Refresh Token](https://github.com/ivanvermeyen/laravel-google-drive-demo/blob/master/README/2-getting-your-refresh-token.md)
-   [Getting your Root Folder ID](https://github.com/ivanvermeyen/laravel-google-drive-demo/blob/master/README/3-getting-your-root-folder-id.md)

## Update `.env` file

Add the keys you created to your `.env` file and set `google` as your default cloud storage. You can copy the [`.env.example`](.env.example) file and fill in the blanks.

```
FILESYSTEM_CLOUD=google
GOOGLE_DRIVE_CLIENT_ID=xxx.apps.googleusercontent.com
GOOGLE_DRIVE_CLIENT_SECRET=xxx
GOOGLE_DRIVE_REFRESH_TOKEN=xxx
GOOGLE_DRIVE_FOLDER_ID=null
#GOOGLE_DRIVE_TEAM_DRIVE_ID=xxx # uncomment if you use team drive
```
Setup email for notifications:
```
MAIL_MAILER=smtp
MAIL_HOST=mailhog
MAIL_PORT=1025
MAIL_USERNAME=your-user
MAIL_PASSWORD=your-passwd
MAIL_ENCRYPTION=tls
MAIL_FROM_ADDRESS=your-address

MAIL_TO_ADDRESS=receive-notifications-address
```
## Taking backups
You can backup your app by running:
```php
php artisan backup:run
```
Backup without notifications:
```php
php artisan backup:run --disable-notifications
```
## Reference
- [Laravel & Google Drive Storage](https://github.com/ivanvermeyen/laravel-google-drive-demo)
- [Spatie Laravel backup](https://spatie.be/docs/laravel-backup/v8/introduction)
- [nao-pon/flysystem-google-drive](https://packagist.org/packages/nao-pon/flysystem-google-drive)
## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
