# Hashing
This Package provides secure Bcrypt and Argon2 hashing for storing user passwords.

!!! warning
    The Argon2i driver requires PHP 7.2.0 or greater and the Argon2id
    driver requires PHP 7.3.0 or greater.


## Configuration

The default `hashing` adapter in config file `Config/App.php` is set `bcrypt` 
!!! info
    Bcrypt is a great choice for hashing passwords because its "work factor" is adjustable, which means that the time it takes to generate a hash can be increased as hardware power increases.

There are few other config option are availabe `cost` option for `bcrypt` adapter, `memory`, `thread` and `time` for `argon's`.

## Basic Usage
You may hash a password by calling the `make` method on the Hashing Class:

```php
<?php 
use Zest\Hashing\Hashing;

$hashing = new Hashing();

//Original password
$password = 123456;
//Hash the password
$password_hash = $hashing->make($password);
echo $password_hash;
```
### Adjusting The Bcrypt Work Factor
If you are using the Bcrypt algorithm, the `make` method allows you to manage the work factor of the algorithm using the  cost option:

```php
$hashing = new Hashing('bcrypt');
$password_hash = $hashing->make($password, [
    'cost' => 12
]);
```
### Adjusting The Argon2 Work Factor
If you are using the Argon2I or Argon2Id algorithm, the `make` method allows you to manage the work factor of the algorithm using the  memory, time, and threads options:

```php
$hashing = new Hashing('argon2i');
$password_hash = $hashing->make($password, [
    'memory' => 1024,
    'time' => 2,
    'threads' => 2,
]);
```

!!! info
    For more information on these options, check out the  [official PHP documentation](https://secure.php.net/manual/en/function.password-hash.php).
 
### Verifying A Password Against A Hash
The `verify` method allows you to verify that a given plain-text string corresponds to a given hash
```php
if ($hashing->verify($password,$password_hash)) {
	//The password matched.
}
```

### Checking If A Password Needs To Be Rehashed
The `needsRehash` function allows you to determine if the work factor used by the hashing has changed since the password was hashed:

```php
if ($hashing->needsRehash($hashed)) {
    $password_hash = $hashing->make($password);
}
```

## Supported algorithm
in this library three algorithm are supported
- Bcrypt
- Argon2I
- Argon2ID

### Switch between algorithm 
```php
$hashing = new Hashing('supported-algorithm');
$bvcryptHashing = new Hashing('bcrypt');
```

#### Default work factors
You can provide default work factors like
```php

//Argon2
$argon2Hashing = new Hashing('argon2i',[
    'memory' => 1024,
    'time' => 2,
    'threads' => 2,
    'verify' => false,
]);

//Bcrypt
$vcryptHashing = new Hashing('bcrypt'[
    'cost' => 12,
    'verify' => false,
]);
```
here verify option is additional indicate that if this set to true the algorithm is also sticky check on verify, if both algorithm are not matched then means password is not correct.
