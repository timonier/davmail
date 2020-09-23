# README

POP / IMAP / SMTP / Caldav / Carddav / LDAP Exchange Gateway

⚠️ This project is no longer maintained. ⚠️

## Usage

Run the application via `docker run`. [OWA](https://en.wikipedia.org/wiki/Outlook_on_the_web) URL and Davmail ports can be passed as environment variables:

```sh
docker run --env PORT_CALDAV=2080 --env PORT_IMAP=2143 --env PORT_LDAP=2389 --env PORT_POP=2110 --env PORT_SMTP=2025 --env URL="https://YOUR-OWA-URL" --net host --rm timonier/davmail
```

__Note__: The environment variables `PORT_*` are not mandatories. The default values for these variables are the values used in the [documentation](http://davmail.sourceforge.net/serversetup.html).

## Links

* [command "docker run"](https://docs.docker.com/reference/run/)
* [davmail](http://davmail.sourceforge.net/)
* [davmail setup as a standalone server](http://davmail.sourceforge.net/serversetup.html)
* [image "timonier/davmail"](https://hub.docker.com/r/timonier/davmail/)
* [just-containers/s6-overlay](https://github.com/just-containers/s6-overlay)
* [jwilder/dockerize](https://github.com/jwilder/dockerize)
* [owa](https://en.wikipedia.org/wiki/Outlook_on_the_web)
* [timonier/dumb-entrypoint](https://github.com/timonier/dumb-entrypoint)
* [timonier/version-lister](https://github.com/timonier/version-lister)
