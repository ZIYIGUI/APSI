# List of Changes

## Version 0.7.0

- The CMake system no longer builds unit tests and the CLI by default.
To build these, specify `-DAPSI_BUILD_CLI=ON` and `-DAPSI_BUILD_TESTS=ON`.

## Version 0.6.0

- The function `SenderDB::strip` now also clears the OPRF key from held by the `SenderDB` instance.
This can be useful in some situations, where the `SenderDB` should serve query requests in an untrusted environment and should have no access to the OPRF key.
Note that the OPRF requests still need to be served and do require the OPRF key, but this can be done, for example, by a different isolated machine.
It is essential to ensure that the OPRF key is saved before calling `SenderDB::strip`.
- Removed `parameters/16M-256.json`; use [parameters/16M-1024.json](parameters/16M-1024.json) instead.
- Added error handling code in [sender/apsi/zmq/sender_dispatcher.cpp](sender/apsi/zmq/sender_dispatcher.cpp).

## Version 0.5.0

- Added flexibility to use *any* value for `felts_per_item` in `PSIParams`, not just a power of two.
- Corrected parameter files to have < 2^(-40) false-positive probability per protocol execution.
