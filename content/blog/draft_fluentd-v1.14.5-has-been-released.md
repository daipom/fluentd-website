# Fluentd v1.14.5 has been released

Hi users!

We have released v1.14.5. ChangeLog is [here](https://github.com/fluent/fluentd/blob/master/CHANGELOG.md#v1145).

This release is a maintenance release of v1.14 series.

### `in_http`: Add support for "application/x-ndjson"

In this release, `in_http` supports the new Content-Type "application/x-ndjson".
Its format is "ndjson", which is basically a list of JSON objects separated by "\n".

Here is an example of the format.

```json
{"foo": "bar"}
{"buz": "hoge"}
```

See [#3616](https://github.com/fluent/fluentd/pull/3616) for more information.

### Add support for the UCRT binary for Windows RubyInstaller 3.1

RubyInstaller 3.1 has switched C-Runtime from MSVCRT to UCRT, and the ruby and
gem platform has changed to `x64-mingw-ucrt`.
There was a problem in this environment that Windows-specific dependent gems
could not be installed because Fluentd for this architecture had not been released.

Beginning with this release, Fluentd for this architecture is also released
and this problem is solved.

See [#3613](https://github.com/fluent/fluentd/pull/3613) for more information.

### `out_forward`: Fix hang-up issue during TLS handshake

There was a known issue the TLS handshake takes a long time or hangs when
`out_forward` uses TLS transport, even though `connect_timeout` is specified.

With this release, `connect_timeout` is now reliably applied to TLS transport
and able to prevent hangs.

See [#3601](https://github.com/fluent/fluentd/pull/3601) for more information.

### Miscellaneous fixes

* Fix a bug of retrying once when `retry_max_times` is `0`. [#3608](https://github.com/fluent/fluentd/pull/3608)
* Fix "invalid byte sequence is replaced" warning not to write out invalid characters. [#3596](https://github.com/fluent/fluentd/pull/3596)
* Bump up required ServerEngine to v2.2.5. [#3599](https://github.com/fluent/fluentd/pull/3599)

Enjoy logging!

TAG: Fluentd Announcement
AUTHOR: clearcode
