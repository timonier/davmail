# README

POP / IMAP / SMTP / Caldav / Carddav / LDAP Exchange Gateway

## Usage

Run the application via `docker run`. [OWA](https://en.wikipedia.org/wiki/Outlook_on_the_web) URL and Davmail ports can be passed as environment variables:

```sh
docker run \
    --env PORT_CALDAV=2080 \
    --env PORT_IMAP=2143 \
    --env PORT_LDAP=2389 \
    --env PORT_POP=2110 \
    --env PORT_SMTP=2025 \
    --env URL="https://YOUR-OWA-URL" \
    --net host \
    timonier/davmail
```

__Note__: The environment variables `PORT_*` are not mandatory. The default values for these variables are the values used in the [documentation](http://davmail.sourceforge.net/serversetup.html).

## Contributing

1. Fork it.
2. Create your branch: `git checkout -b my-new-feature`.
3. Commit your changes: `git commit -am 'Add some feature'`.
4. Push to the branch: `git push origin my-new-feature`.
5. Submit a pull request.

__Note__: Use the script `bin/build` to test your modifications locally.

## Links

* [davmail](http://davmail.sourceforge.net/)
* [davmail setup as a standalone server](http://davmail.sourceforge.net/serversetup.html)
* [command "docker run"](https://docs.docker.com/reference/run/)
* [image "timonier/davmail"](https://hub.docker.com/r/timonier/davmail/)
* [owa](https://en.wikipedia.org/wiki/Outlook_on_the_web)
* [timonier/dumb-entrypoint](https://github.com/timonier/dumb-entrypoint)
* [timonier/version-lister](https://github.com/timonier/version-lister)
