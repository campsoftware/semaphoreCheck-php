# semaphoreCheck-php

### Summary

Gets a semephore and attempts to aquire to prevent code from running more than one time.
- Aborts if the semaphore cannot be retrieved.
- Aborts if the semaphore in use.
- The key must be an integer.

### Calling Example

```php
// Semaphore Check
$semaphoreKey = 42 );
$semaphore = sem_get( $semaphoreKey, 1, 0666, 1 );
if ( $semaphore === false ) {
    $response[ 'Error' ] = 'SEMAPHORE NOT AVAILABLE';
    return;
} else {
    if ( sem_acquire( $semaphore, true ) === false ) {
        $response[ 'Error' ] = 'SEMAPHORE IN USE';
        return;
    }
}
// Semaphore Release Exclusive Control, but will auto release.
$semaphoreReleased = sem_release( $semaphore );
```
