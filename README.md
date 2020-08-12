# semaphoreCheck-php

### Summary

Retrieves the GPS coordinates of the Browser.
- Uses an inline callback.
- Normalizes the output.
- Makes the async call **feel** like a sync call, but it's still async.
- This is a good template for similar async calls.

### Calling Example

```javascript
// Semaphore Check
$semaphoreKey = \xan\xanAsciiSum( basename( __FILE__ ) );
$semaphore = sem_get( $semaphoreKey, 1, 0666, 1 );
if ( $semaphore === false ) {
    $response[ 'Error' ] = 'SEMAPHORE NOT AVAILABLE';
    $aloe_response->content_set( json_encode( $response ) );
    return;
} else {
    if ( sem_acquire( $semaphore, true ) === false ) {
        $response[ 'Error' ] = 'SEMAPHORE IN USE';
        $aloe_response->content_set( json_encode( $response ) );
        return;
    }
}
// Semaphore Release Exclusive Control, but will auto release.
// $semaphoreReleased = sem_release( $semaphore );
```
