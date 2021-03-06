# semaphoreCheck-php

### Summary

Gets a semaphore and attempts to acquire to prevent code from running more than one time.
- Aborts if the semaphore cannot be retrieved.
- Aborts if the semaphore in use.
- The key must be an integer.

### Code

```php
// Semaphore Check
$semaphoreKey = 42 );
$semaphore = sem_get( $semaphoreKey, 1, 0666, 1 );
if ( $semaphore === false ) {
    $response[ 'Error' ] = 'SEMAPHORE NOT AVAILABLE';
    return;
} else {
    // Pass true to return false if in use. Omit to pause until not blocked.
    if ( sem_acquire( $semaphore, true ) === false ) {
        $response[ 'Error' ] = 'SEMAPHORE IN USE';
        return;
    }
}
// Semaphore Release Exclusive Control, but will auto release.
$semaphoreReleased = sem_release( $semaphore );
```
