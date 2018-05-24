# Laravel Backup Shield

[![Latest Version on Packagist][ico-version]][link-packagist]
[![Software License][ico-license]](LICENSE.md)
[![Build Status][ico-travis]][link-travis]

## Secure your backups

This package helps your encrypt and password protect your backups taken with [Spatie's](https://github.com/spatie) fantastic [Laravel-backup package](https://github.com/spatie/laravel-backup).

Backup Shield simply listens for when the .zip-file generated by Laravel-backup is done, then grabs it and applies your password and encryption of your liking.

## Installation

`composer require olssonm\laravel-backup-shield`

Currently tested with `spatie/laravel-backup` >= 5.0 and `laravel/framework` >= 5.2.

## Configuration

You only have the option to set two different options; password and encryption.

```php
// Default configuration; backup-shield.php
return [
    'password' => config('app.key'),
    'encryption' => \Olssonm\BackupShield\Encryption::ENCRYPTION_DEFAULT
];
```

**Password**

Your password (*duh*). The default is the application key (`APP_KEY` in your .env-file). You might want to set something more appropriate.

Set to `NULL` if you want to keep your backup without a password.

**Encryption**

Set your type of encryption. Available options are:

`\Olssonm\BackupShield\ENCRYPTION_DEFAULT` (PKWARE/ZipCrypto)  
`\Olssonm\BackupShield\ENCRYPTION_WINZIP_AES_128` (AES 128)  
`\Olssonm\BackupShield\ENCRYPTION_WINZIP_AES_192` (AES 192)  
`\Olssonm\BackupShield\ENCRYPTION_WINZIP_AES_256` (AES 256)  

Note that macOS among other does *not* support the Winzip AES-encryption methods as standard. You might have to buy a seperate app and/or license to decrypt and open the protected file. However, if you have the option for AES 256 you should go with that as ZipCrypto may be weak.

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

© 2018 [Marcus Olsson](https://marcusolsson.me).

[ico-version]: https://img.shields.io/packagist/v/olssonm/laravel-backup-shield.svg?style=flat-square
[ico-license]: https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square
[ico-travis]: https://img.shields.io/travis/olssonm/laravel-backup-shield/master.svg?style=flat-square
[ico-downloads]: https://img.shields.io/packagist/dt/olssonm/laravel-backup-shield.svg?style=flat-square
[link-packagist]: https://packagist.org/packages/olssonm/laravel-backup-shield
[link-travis]: https://travis-ci.org/olssonm/laravel-backup-shield
