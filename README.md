# phoebus-site

The public asset site for [Phoebus](https://github.com/pendo324/Phoebus),
a native iOS Reddit client. It is static HTML with no scripts, no trackers
and no third-party requests, published with GitHub Pages from `main`:

- `/` — what Phoebus is, and the unaffiliation note
- `/privacy.html` — what the app sends, stores and asks for
- `/phoebus-icon.png` — the Bark notification icon

## The notification icon

Bark fetches its notification icon by URL, so an app that wants its own icon
on Bark notifications has to point at something on the web. `phoebus-icon.png`
is that file, and the app's `PushNotificationClient.defaultIconURL` points at
this site's copy of it.

To replace it, render the app's icon artwork from a Phoebus checkout and copy
the result over the same filename:

```sh
# in a Phoebus checkout, with Go and rsvg-convert installed
.build/lgrender -icon Icons/LiquidGlass/phoebus/phoebus/phoebus.icon \
    -o /path/to/phoebus-site/phoebus-icon.png -size 180
git commit -am "Update the notification icon" && git push
```

Push to `main` and Pages republishes within a minute or two. Nothing in the
app needs rebuilding: the URL is a constant, so the new bytes are picked up
by the next notification.

## Licence

The icon is Phoebus's own artwork. The site's content is released under the
GNU GPL version 3, matching the app.

Nothing here should name or link the maintainer's private hosts, home
network or machine; this site is public.