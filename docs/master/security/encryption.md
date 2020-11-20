# Encryption
Encryption library bundled with Zest.

## Configuration

The default `encryption` adapter in config file `Config/App.php` is set `openssl`

!!! warning
    You should change encryption your `key`

## Encrypt
You can encrypt string by calling to encrypt method

```php 
<?php 
use Zest\Encryption\Encryption;

$encryption = new Encryption('your-key'); // key is optional

//Encrypt the message
$encrypt = $encryption->encrypt("This is a text");

echo $encrypt;
```

### Decrypt
You can decrypt token by calling decrypt method 

```php 
<?php 
$encryption = new Encryption('your-key');

//Decrypt the message
$decrypt = $encryption->decrypt($encrypt);	
echo $decrypt;
```

### Adapter
This Package support two encryption adapter
- OpenSSL
- Sodium


### change Adapter
You can pass supported adapter to class like

Use of sodium
```php 
<?php 
$encryption = new Encryption('your-key','sodium');
```

!!! info
    Sodium php extension is required.


Use of openSSL

!!! info
    The adapter can also be changed from `Config/App.php` file.


```php 
<?php 
$encryption = new Encryption('your-key','openssl');
```

!!! info
    openSSL php extension is required.
