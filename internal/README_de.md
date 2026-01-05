# `/internal`

Privater Anwendungs- und Bibliothekscode. Dies ist der Code, den Sie nicht möchten, dass andere in ihre Anwendungen oder Bibliotheken importieren. Beachten Sie, dass dieses Layoutmuster vom Go-Compiler selbst erzwungen wird. Siehe die Go 1.4 [`release notes`](https://golang.org/doc/go1.4#internalpackages) für weitere Details. Beachten Sie, dass Sie nicht auf das oberste `internal` Verzeichnis beschränkt sind. Sie können mehr als ein `internal` Verzeichnis auf jeder Ebene Ihres Projektbaums haben.

Sie können optional etwas zusätzliche Struktur zu Ihren internen Paketen hinzufügen, um Ihren gemeinsam genutzten und nicht gemeinsam genutzten internen Code zu trennen. Es ist nicht erforderlich (besonders für kleinere Projekte), aber es ist schön, visuelle Hinweise zu haben, die die beabsichtigte Paketnutzung zeigen. Ihr tatsächlicher Anwendungscode kann in das `/internal/app` Verzeichnis gehen (z.B. `/internal/app/myapp`) und der von diesen Apps gemeinsam genutzte Code in das `/internal/pkg` Verzeichnis (z.B. `/internal/pkg/myprivlib`).

Beispiele:

* https://github.com/hashicorp/terraform/tree/main/internal
* https://github.com/influxdata/influxdb/tree/master/internal
* https://github.com/perkeep/perkeep/tree/master/internal
* https://github.com/jaegertracing/jaeger/tree/main/internal
* https://github.com/moby/moby/tree/master/internal
* https://github.com/satellity/satellity/tree/main/internal
* https://github.com/minio/minio/tree/master/internal

## `/internal/pkg`

Beispiele:

* https://github.com/hashicorp/waypoint/tree/main/internal/pkg
