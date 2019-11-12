# Send a welcome notification to new users

[![Latest Version on Packagist](https://img.shields.io/packagist/v/spatie/laravel-welcome-mail.svg?style=flat-square)](https://packagist.org/packages/spatie/laravel-welcome-mail)
[![Build Status](https://img.shields.io/travis/spatie/laravel-welcome-mail/master.svg?style=flat-square)](https://travis-ci.org/spatie/laravel-welcome-mail)
[![Quality Score](https://img.shields.io/scrutinizer/g/spatie/laravel-welcome-mail.svg?style=flat-square)](https://scrutinizer-ci.com/g/spatie/laravel-welcome-mail)
[![Total Downloads](https://img.shields.io/packagist/dt/spatie/laravel-welcome-mail.svg?style=flat-square)](https://packagist.org/packages/spatie/laravel-welcome-mail)

Using this package you can send a `WelcomeNotification` to a new user of your app. The notification contain a link to a screen where the user can set an initial password.

```php
$user->notify(new Spatie\WelcomeNotification\WelcomeNotification());
```

## Installation

You can install the package via composer:

```bash
composer require spatie/laravel-welcome-mail
```

Next you must use this macro somewhere in your routes file.

```php
Route::handleWelcome();
```

The package ships with two views you should style yourself. You can publish the views with this command:

```bash
php artisan vendor:publish --provider="Spatie\WelcomeNotification\WelcomeNotificationServiceProvider" --tag="views"
```

The `welcome` view will be rendered when somebody click the welcome link in the welcome notification mail. The `invalidWelcomeLink` will be rendered whenever somebody clicks an invalid welcome link.

## Usage

Here's how you can send a welcome notification to a user that you just created.

```php
$user->notify(new Spatie\WelcomeNotification\WelcomeNotification());
```

By default the `WelcomeNotification` will send a mail. If you wish to customize the mail you can extend `WelcomeNotification` and override the `buildWelcomeNotificationMessage` method.

```php
class MyCustomWelcomeNotification extends WelcomeNotification
{
    public function buildWelcomeNotificationMessage(): Illuminate\Notifications\Messages\MailMessage
    {
        return (new MailMessage)
            ->subject('Welcome to my app')
            ->action(Lang::get('Set initial password'), $this->showWelcomeFormUrl)
    }
}
```

### Testing

```bash
composer test
```

### Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

### Security

If you discover any security related issues, please email freek@spatie.be instead of using the issue tracker.

## Postcardware

You're free to use this package, but if it makes it to your production environment we highly appreciate you sending us a postcard from your hometown, mentioning which of our package(s) you are using.

Our address is: Spatie, Samberstraat 69D, 2060 Antwerp, Belgium.

We publish all received postcards [on our company website](https://spatie.be/en/opensource/postcards).

## Credits

- [Freek Van der HErten](https://github.com/freekmurze)
- [All Contributors](../../contributors)

## Support us

Spatie is a webdesign agency based in Antwerp, Belgium. You'll find an overview of all our open source projects [on our website](https://spatie.be/opensource).

Does your business depend on our contributions? Reach out and support us on [Patreon](https://www.patreon.com/spatie). 
All pledges will be dedicated to allocating workforce on maintenance and new awesome stuff.

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
