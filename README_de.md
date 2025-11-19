# Standard Go Projektstruktur

Übersetzungen:

* [English](README.md)
* [한국어 문서](README_ko.md)
* [简体中文](README_zh.md)
* [正體中文](README_zh-TW.md)
* [简体中文](README_zh-CN.md) - ???
* [Français](README_fr.md)
* [日本語](README_ja.md)
* [Português](README_ptBR.md)
* [Español](README_es.md)
* [Română](README_ro.md)
* [Русский](README_ru.md)
* [Türkçe](README_tr.md)
* [Italiano](README_it.md)
* [Tiếng Việt](README_vi.md)
* [Українська](README_ua.md)
* [Indonesian](README_id.md)
* [हिन्दी](README_hi.md)
* [فارسی](README_fa.md)
* [Беларуская](README_be.md)
* [বাংলা](README_bn.md)
* [Deutsch](README_de.md)

## Überblick

Dies ist eine grundlegende Struktur für Go-Anwendungsprojekte. Beachten Sie, dass sie grundlegend ist, was den Inhalt betrifft, da sie sich nur auf das allgemeine Layout konzentriert und nicht auf das, was Sie darin haben. Sie ist auch grundlegend, weil sie sehr allgemein gehalten ist und nicht ins Detail geht, wie Sie Ihr Projekt noch weiter strukturieren können. Zum Beispiel versucht sie nicht, die Projektstruktur abzudecken, die Sie mit etwas wie Clean Architecture hätten.

Dies ist **`KEIN offizieller Standard, der vom Kern-Go-Entwicklungsteam definiert wurde`**. Dies ist eine Sammlung gängiger historischer und aufkommender Projektlayoutmuster im Go-Ökosystem. Einige dieser Muster sind beliebter als andere. Es enthält auch eine Reihe kleiner Verbesserungen zusammen mit mehreren unterstützenden Verzeichnissen, die für jede ausreichend große reale Anwendung üblich sind. Beachten Sie, dass das **Kern-Go-Team großartige allgemeine Richtlinien zur Strukturierung von Go-Projekten bereitstellt** und was es für Ihr Projekt bedeutet, wenn es importiert und installiert wird. Siehe die Seite [`Organizing a Go module`](https://go.dev/doc/modules/layout) in der offiziellen Go-Dokumentation für weitere Details. Sie enthält die `internal` und `cmd` Verzeichnismuster (unten beschrieben) und andere nützliche Informationen.

**`Wenn Sie versuchen, Go zu lernen oder wenn Sie einen PoC oder ein einfaches Projekt für sich selbst erstellen, ist diese Projektstruktur übertrieben. Beginnen Sie stattdessen mit etwas wirklich Einfachem (eine einzige `main.go` Datei und `go.mod` ist mehr als genug).`** Wenn Ihr Projekt wächst, denken Sie daran, dass es wichtig ist, sicherzustellen, dass Ihr Code gut strukturiert ist, sonst enden Sie mit unordentlichem Code mit vielen versteckten Abhängigkeiten und globalem Zustand. Wenn Sie mehr Leute am Projekt arbeiten haben, benötigen Sie noch mehr Struktur. Dann ist es wichtig, eine gemeinsame Methode zur Verwaltung von Paketen/Bibliotheken einzuführen. Wenn Sie ein Open-Source-Projekt haben oder wenn Sie wissen, dass andere Projekte den Code aus Ihrem Projekt-Repository importieren, ist es wichtig, private (aka `internal`) Pakete und Code zu haben. Klonen Sie das Repository, behalten Sie, was Sie brauchen, und löschen Sie alles andere! Nur weil es da ist, heißt das nicht, dass Sie alles verwenden müssen. Keines dieser Muster wird in jedem einzelnen Projekt verwendet. Selbst das `vendor` Muster ist nicht universell.

Mit Go 1.14 sind [`Go Modules`](https://go.dev/wiki/Modules) endlich bereit für die Produktion. Verwenden Sie [`Go Modules`](https://blog.golang.org/using-go-modules), es sei denn, Sie haben einen bestimmten Grund, sie nicht zu verwenden. Wenn Sie dies tun, müssen Sie sich keine Gedanken über $GOPATH und darüber machen, wo Sie Ihr Projekt ablegen. Die grundlegende `go.mod` Datei im Repository geht davon aus, dass Ihr Projekt auf GitHub gehostet wird, aber es ist keine Voraussetzung. Der Modulpfad kann alles sein, obwohl die erste Modulpfadkomponente einen Punkt im Namen haben sollte (die aktuelle Version von Go erzwingt dies nicht mehr, aber wenn Sie etwas ältere Versionen verwenden, wundern Sie sich nicht, wenn Ihre Builds ohne ihn fehlschlagen). Siehe Issues [`37554`](https://github.com/golang/go/issues/37554) und [`32819`](https://github.com/golang/go/issues/32819), wenn Sie mehr darüber erfahren möchten.

Diese Projektstruktur ist absichtlich generisch und versucht nicht, eine bestimmte Go-Paketstruktur vorzuschreiben.

Dies ist ein Gemeinschaftsprojekt. Öffnen Sie ein Issue, wenn Sie ein neues Muster sehen oder wenn Sie denken, dass eines der bestehenden Muster aktualisiert werden muss.

Wenn Sie Hilfe bei der Benennung, Formatierung und dem Stil benötigen, beginnen Sie mit der Ausführung von [`gofmt`](https://golang.org/cmd/gofmt/) und [`staticcheck`](https://github.com/dominikh/go-tools/tree/master/cmd/staticcheck). Der vorherige Standard-Linter, golint, ist jetzt veraltet und wird nicht mehr gewartet; die Verwendung eines gewarteten Linters wie staticcheck wird empfohlen. Stellen Sie außerdem sicher, dass Sie diese Go-Codestilrichtlinien und -empfehlungen lesen:
* https://talks.golang.org/2014/names.slide
* https://golang.org/doc/effective_go.html#names
* https://blog.golang.org/package-names
* https://go.dev/wiki/CodeReviewComments
* [Style guideline for Go packages](https://rakyll.org/style-packages) (rakyll/JBD)

Siehe [`Go Project Layout`](https://medium.com/golang-learn/go-project-layout-e5213cdcfaa2) für zusätzliche Hintergrundinformationen.

Mehr über die Benennung und Organisation von Paketen sowie andere Empfehlungen zur Codestruktur:
* [GopherCon EU 2018: Peter Bourgon - Best Practices for Industrial Programming](https://www.youtube.com/watch?v=PTE4VJIdHPg)
* [GopherCon Russia 2018: Ashley McNamara + Brian Ketelsen - Go best practices.](https://www.youtube.com/watch?v=MzTcsI6tn-0)
* [GopherCon 2017: Edward Muller - Go Anti-Patterns](https://www.youtube.com/watch?v=ltqV6pDKZD8)
* [GopherCon 2018: Kat Zien - How Do You Structure Your Go Apps](https://www.youtube.com/watch?v=oL6JBUk6tj0)

Ein chinesischer Beitrag über Package-Oriented-Design-Richtlinien und Architekturschichten
* [面向包的设计和架构分层](https://github.com/danceyoung/paper-code/blob/master/package-oriented-design/packageorienteddesign.md)

## Go Verzeichnisse

### `/cmd`

Hauptanwendungen für dieses Projekt.

Der Verzeichnisname für jede Anwendung sollte mit dem Namen der ausführbaren Datei übereinstimmen, die Sie haben möchten (z.B. `/cmd/myapp`).

Setzen Sie nicht viel Code in das Anwendungsverzeichnis. Wenn Sie denken, dass der Code importiert und in anderen Projekten verwendet werden kann, sollte er im `/pkg` Verzeichnis liegen. Wenn der Code nicht wiederverwendbar ist oder wenn Sie nicht möchten, dass andere ihn wiederverwenden, setzen Sie diesen Code in das `/internal` Verzeichnis. Sie werden überrascht sein, was andere tun werden, also seien Sie explizit über Ihre Absichten!

Es ist üblich, eine kleine `main` Funktion zu haben, die Code aus den `/internal` und `/pkg` Verzeichnissen importiert und aufruft und nichts anderes.

Siehe das [`/cmd`](cmd/README.md) Verzeichnis für Beispiele.

### `/internal`

Privater Anwendungs- und Bibliothekscode. Dies ist der Code, den Sie nicht möchten, dass andere in ihre Anwendungen oder Bibliotheken importieren. Beachten Sie, dass dieses Layoutmuster vom Go-Compiler selbst erzwungen wird. Siehe die Go 1.4 [`release notes`](https://golang.org/doc/go1.4#internalpackages) für weitere Details. Beachten Sie, dass Sie nicht auf das oberste `internal` Verzeichnis beschränkt sind. Sie können mehr als ein `internal` Verzeichnis auf jeder Ebene Ihres Projektbaums haben.

Sie können optional etwas zusätzliche Struktur zu Ihren internen Paketen hinzufügen, um Ihren gemeinsam genutzten und nicht gemeinsam genutzten internen Code zu trennen. Es ist nicht erforderlich (besonders für kleinere Projekte), aber es ist schön, visuelle Hinweise zu haben, die die beabsichtigte Paketnutzung zeigen. Ihr tatsächlicher Anwendungscode kann in das `/internal/app` Verzeichnis gehen (z.B. `/internal/app/myapp`) und der von diesen Apps gemeinsam genutzte Code in das `/internal/pkg` Verzeichnis (z.B. `/internal/pkg/myprivlib`).

Sie verwenden internal Verzeichnisse, um Pakete privat zu machen. Wenn Sie ein Paket in ein internal Verzeichnis setzen, können andere Pakete es nicht importieren, es sei denn, sie teilen einen gemeinsamen Vorfahren. Und es ist das einzige Verzeichnis, das in der Go-Dokumentation genannt wird und eine spezielle Compiler-Behandlung hat.

### `/pkg`

Bibliothekscode, der von externen Anwendungen verwendet werden darf (z.B. `/pkg/mypubliclib`). Andere Projekte werden diese Bibliotheken importieren und erwarten, dass sie funktionieren, also denken Sie zweimal nach, bevor Sie etwas hier ablegen :-) Beachten Sie, dass das `internal` Verzeichnis ein besserer Weg ist, um sicherzustellen, dass Ihre privaten Pakete nicht importierbar sind, weil es von Go erzwungen wird. Das `/pkg` Verzeichnis ist immer noch ein guter Weg, um explizit zu kommunizieren, dass der Code in diesem Verzeichnis sicher von anderen verwendet werden kann. Der [`I'll take pkg over internal`](https://travisjeffery.com/b/2019/11/i-ll-take-pkg-over-internal/) Blogbeitrag von Travis Jeffery bietet einen guten Überblick über die `pkg` und `internal` Verzeichnisse und wann es sinnvoll sein könnte, sie zu verwenden.

Es ist auch eine Möglichkeit, Go-Code an einem Ort zu gruppieren, wenn Ihr Root-Verzeichnis viele Nicht-Go-Komponenten und Verzeichnisse enthält, was es einfacher macht, verschiedene Go-Tools auszuführen (wie in diesen Vorträgen erwähnt: [`Best Practices for Industrial Programming`](https://www.youtube.com/watch?v=PTE4VJIdHPg) von GopherCon EU 2018, [GopherCon 2018: Kat Zien - How Do You Structure Your Go Apps](https://www.youtube.com/watch?v=oL6JBUk6tj0) und [GoLab 2018 - Massimiliano Pippi - Project layout patterns in Go](https://www.youtube.com/watch?v=3gQa1LWwuzk)).

Siehe das [`/pkg`](pkg/README.md) Verzeichnis, wenn Sie sehen möchten, welche beliebten Go-Repos dieses Projektlayoutmuster verwenden. Dies ist ein gängiges Layoutmuster, aber es ist nicht universell akzeptiert und einige in der Go-Community empfehlen es nicht.

Es ist in Ordnung, es nicht zu verwenden, wenn Ihr App-Projekt wirklich klein ist und eine zusätzliche Verschachtelungsebene nicht viel Wert hinzufügt (es sei denn, Sie möchten es wirklich :-)). Denken Sie darüber nach, wenn es groß genug wird und Ihr Root-Verzeichnis ziemlich voll wird (besonders wenn Sie viele Nicht-Go-App-Komponenten haben).

Die Ursprünge des `pkg` Verzeichnisses: Der alte Go-Quellcode verwendete `pkg` für seine Pakete und dann begannen verschiedene Go-Projekte in der Community, das Muster zu kopieren (siehe [`diesen`](https://twitter.com/bradfitz/status/1039512487538970624) Tweet von Brad Fitzpatrick für mehr Kontext).

### `/vendor`

Anwendungsabhängigkeiten (manuell verwaltet oder von Ihrem bevorzugten Dependency-Management-Tool wie dem neuen eingebauten [`Go Modules`](https://go.dev/wiki/Modules) Feature). Der `go mod vendor` Befehl erstellt das `/vendor` Verzeichnis für Sie. Beachten Sie, dass Sie möglicherweise das `-mod=vendor` Flag zu Ihrem `go build` Befehl hinzufügen müssen, wenn Sie nicht Go 1.14 verwenden, wo es standardmäßig aktiviert ist.

Committen Sie Ihre Anwendungsabhängigkeiten nicht, wenn Sie eine Bibliothek erstellen.

Beachten Sie, dass Go seit [`1.13`](https://golang.org/doc/go1.13#modules) auch das Modul-Proxy-Feature aktiviert hat (unter Verwendung von [`https://proxy.golang.org`](https://proxy.golang.org) als ihrem Modul-Proxy-Server standardmäßig). Lesen Sie mehr darüber [`hier`](https://blog.golang.org/module-mirror-launch), um zu sehen, ob es alle Ihre Anforderungen und Einschränkungen erfüllt. Wenn ja, dann benötigen Sie das `vendor` Verzeichnis überhaupt nicht.

## Service Anwendungsverzeichnisse

### `/api`

OpenAPI/Swagger Spezifikationen, JSON Schema Dateien, Protokolldefinitionsdateien.

Siehe das [`/api`](api/README.md) Verzeichnis für Beispiele.

## Web Anwendungsverzeichnisse

### `/web`

Webанwendungsspezifische Komponenten: statische Web-Assets, serverseitige Templates und SPAs.

## Allgemeine Anwendungsverzeichnisse

### `/configs`

Konfigurationsdateivorlagen oder Standardkonfigurationen.

Legen Sie Ihre `confd` oder `consul-template` Vorlagendateien hier ab.

### `/init`

System init (systemd, upstart, sysv) und Prozessmanager/Supervisor (runit, supervisord) Konfigurationen.

### `/scripts`

Skripte zur Durchführung verschiedener Build-, Installations-, Analyse- usw. Operationen.

Diese Skripte halten das Makefile auf oberster Ebene klein und einfach (z.B. [`https://github.com/hashicorp/terraform/blob/main/Makefile`](https://github.com/hashicorp/terraform/blob/main/Makefile)).

Siehe das [`/scripts`](scripts/README.md) Verzeichnis für Beispiele.

### `/build`

Paketierung und Continuous Integration.

Legen Sie Ihre Cloud (AMI)-, Container (Docker)-, OS (deb, rpm, pkg) Paketkonfigurationen und Skripte in das `/build/package` Verzeichnis.

Legen Sie Ihre CI (travis, circle, drone) Konfigurationen und Skripte in das `/build/ci` Verzeichnis. Beachten Sie, dass einige der CI-Tools (z.B. Travis CI) sehr wählerisch bezüglich des Standorts ihrer Konfigurationsdateien sind. Versuchen Sie, die Konfigurationsdateien in das `/build/ci` Verzeichnis zu legen und sie mit dem Standort zu verknüpfen, an dem die CI-Tools sie erwarten (wenn möglich).

### `/deployments`

IaaS, PaaS, System- und Container-Orchestrierungsbereitstellungskonfigurationen und Vorlagen (docker-compose, kubernetes/helm, terraform). Beachten Sie, dass in einigen Repos (besonders Apps, die mit Kubernetes bereitgestellt werden) dieses Verzeichnis `/deploy` genannt wird.

### `/test`

Zusätzliche externe Test-Apps und Testdaten. Fühlen Sie sich frei, das `/test` Verzeichnis so zu strukturieren, wie Sie möchten. Für größere Projekte macht es Sinn, ein Daten-Unterverzeichnis zu haben. Sie können zum Beispiel `/test/data` oder `/test/testdata` haben, wenn Sie möchten, dass Go ignoriert, was in diesem Verzeichnis ist. Beachten Sie, dass Go auch Verzeichnisse oder Dateien ignoriert, die mit "." oder "_" beginnen, sodass Sie mehr Flexibilität bei der Benennung Ihres Testdatenverzeichnisses haben.

Siehe das [`/test`](test/README.md) Verzeichnis für Beispiele.

## Andere Verzeichnisse

### `/docs`

Design- und Benutzerdokumente (zusätzlich zu Ihrer godoc-generierten Dokumentation).

Siehe das [`/docs`](docs/README.md) Verzeichnis für Beispiele.

### `/tools`

Unterstützende Tools für dieses Projekt. Beachten Sie, dass diese Tools Code aus den `/pkg` und `/internal` Verzeichnissen importieren können.

Siehe das [`/tools`](tools/README.md) Verzeichnis für Beispiele.

### `/examples`

Beispiele für Ihre Anwendungen und/oder öffentlichen Bibliotheken.

Siehe das [`/examples`](examples/README.md) Verzeichnis für Beispiele.

### `/third_party`

Externe Hilfstools, gegabelter Code und andere Drittanbieter-Dienstprogramme (z.B. Swagger UI).

### `/githooks`

Git Hooks.

### `/assets`

Andere Assets, die zu Ihrem Repository gehören (Bilder, Logos usw.).

### `/website`

Dies ist der Ort, um die Website-Daten Ihres Projekts abzulegen, wenn Sie nicht GitHub Pages verwenden.

Siehe das [`/website`](website/README.md) Verzeichnis für Beispiele.

## Verzeichnisse, die Sie nicht haben sollten

### `/src`

Einige Go-Projekte haben einen `src` Ordner, aber das passiert normalerweise, wenn die Entwickler aus der Java-Welt kommen, wo es ein übliches Muster ist. Wenn Sie sich helfen können, versuchen Sie, dieses Java-Muster nicht zu übernehmen. Sie wollen wirklich nicht, dass Ihr Go-Code oder Ihre Go-Projekte wie Java aussehen :-)

Verwechseln Sie nicht das `/src` Verzeichnis auf Projektebene mit dem `/src` Verzeichnis, das Go für seine Workspaces verwendet, wie in [`How to Write Go Code`](https://golang.org/doc/code.html) beschrieben. Die `$GOPATH` Umgebungsvariable zeigt auf Ihren (aktuellen) Workspace (standardmäßig zeigt sie auf `$HOME/go` auf Nicht-Windows-Systemen). Dieser Workspace enthält die obersten `/pkg`, `/bin` und `/src` Verzeichnisse. Ihr tatsächliches Projekt endet als Unterverzeichnis unter `/src`, wenn Sie also das `/src` Verzeichnis in Ihrem Projekt haben, sieht der Projektpfad so aus: `/some/path/to/workspace/src/your_project/src/your_code.go`. Beachten Sie, dass es mit Go 1.11 möglich ist, Ihr Projekt außerhalb Ihres `GOPATH` zu haben, aber das bedeutet immer noch nicht, dass es eine gute Idee ist, dieses Layoutmuster zu verwenden.


## Badges

* [Go Report Card](https://goreportcard.com/) - Es scannt Ihren Code mit `gofmt`, `go vet`, `gocyclo`, `golint`, `ineffassign`, `license` und `misspell`. Ersetzen Sie `github.com/golang-standards/project-layout` durch Ihre Projektreferenz.

    [![Go Report Card](https://goreportcard.com/badge/github.com/golang-standards/project-layout?style=flat-square)](https://goreportcard.com/report/github.com/golang-standards/project-layout)

* ~~[GoDoc](http://godoc.org) - Es stellt eine Online-Version Ihrer GoDoc-generierten Dokumentation bereit. Ändern Sie den Link, um auf Ihr Projekt zu verweisen.~~

    [![Go Doc](https://img.shields.io/badge/godoc-reference-blue.svg?style=flat-square)](http://godoc.org/github.com/golang-standards/project-layout)

* [Pkg.go.dev](https://pkg.go.dev) - Pkg.go.dev ist ein neues Ziel für Go-Entdeckung & Dokumentation. Sie können ein Badge mit dem [Badge-Generator-Tool](https://pkg.go.dev/badge) erstellen.

    [![PkgGoDev](https://pkg.go.dev/badge/github.com/golang-standards/project-layout)](https://pkg.go.dev/github.com/golang-standards/project-layout)

* Release - Es zeigt die neueste Release-Nummer für Ihr Projekt. Ändern Sie den GitHub-Link, um auf Ihr Projekt zu verweisen.

    [![Release](https://img.shields.io/github/release/golang-standards/project-layout.svg?style=flat-square)](https://github.com/golang-standards/project-layout/releases/latest)

## Anmerkungen

Eine meinungsstärkere Projektvorlage mit Beispiel-/wiederverwendbaren Konfigurationen, Skripten und Code ist in Arbeit.
