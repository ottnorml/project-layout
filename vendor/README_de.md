# `/vendor`

Anwendungsabhängigkeiten (manuell verwaltet oder von Ihrem bevorzugten Dependency-Management-Tool oder dem eingebauten [`modules`](https://go.dev/wiki/Modules) Feature).

Committen Sie Ihre Anwendungsabhängigkeiten nicht, wenn Sie eine Bibliothek erstellen.

Beachten Sie, dass Go seit [`1.13`](https://golang.org/doc/go1.13#modules) auch das Modul-Proxy-Feature aktiviert hat (unter Verwendung von `https://proxy.golang.org` als ihrem Modul-Proxy-Server standardmäßig). Lesen Sie mehr darüber [`hier`](https://blog.golang.org/module-mirror-launch), um zu sehen, ob es alle Ihre Anforderungen und Einschränkungen erfüllt. Wenn ja, dann benötigen Sie das 'vendor' Verzeichnis überhaupt nicht.
