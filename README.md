# phoebus-site

The Pages site for [Phoebus](https://github.com/pendo324/Phoebus), an
independent Reddit client for iPhone and iPad.

It exists for one reason beyond a landing page: **it hosts the app's
notification icon.** Bark fetches an icon by URL, so an app that wants its
own icon on Bark notifications has to point at something on the web.
`icon.png` is that file, and the app's
`PushNotificationClient.defaultIconURL` points at:

    https://pendo324.github.io/phoebus-site/icon.png

## Updating the icon

`icon.png` is a 180x180 PNG rendered from the app's own icon artwork in the
Phoebus repository, not drawn here. To regenerate it after the icon changes:

```sh
# in a Phoebus checkout, with Go and rsvg-convert installed
.build/lgrender -icon Icons/LiquidGlass/phoebus/phoebus/phoebus.icon \
    -o /path/to/phoebus-site/icon.png -size 180
git commit -am "Update the notification icon" && git push
```

Push to `main` and Pages republishes within a minute or two. Nothing in the
app needs rebuilding: the URL is a constant, so the new bytes are picked up
by the next notification.

## Licence

The icon is Phoebus's own artwork and this page is released under the GNU GPL
version 3, matching the app. Plain HTML and CSS, no scripts, no trackers, no
third-party requests.