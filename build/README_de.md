# `/build`

Paketierung und Continuous Integration.

Legen Sie Ihre Cloud (AMI)-, Container (Docker)-, OS (deb, rpm, pkg) Paketkonfigurationen und Skripte in das `/build/package` Verzeichnis.

Legen Sie Ihre CI (travis, circle, drone) Konfigurationen und Skripte in das `/build/ci` Verzeichnis. Beachten Sie, dass einige der CI-Tools (z.B. Travis CI) sehr wählerisch bezüglich des Standorts ihrer Konfigurationsdateien sind. Versuchen Sie, die Konfigurationsdateien in das `/build/ci` Verzeichnis zu legen und sie mit dem Standort zu verknüpfen, an dem die CI-Tools sie erwarten, wenn möglich (machen Sie sich keine Sorgen, wenn es nicht möglich ist und wenn das Beibehalten dieser Dateien im Root-Verzeichnis Ihr Leben einfacher macht :-)).

Beispiele:

* https://github.com/cockroachdb/cockroach/tree/master/build
