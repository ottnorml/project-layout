# `/cmd`

Hauptanwendungen für dieses Projekt.

Der Verzeichnisname für jede Anwendung sollte mit dem Namen der ausführbaren Datei übereinstimmen, die Sie haben möchten (z.B. `/cmd/myapp`).

Setzen Sie nicht viel Code in das Anwendungsverzeichnis. Wenn Sie denken, dass der Code importiert und in anderen Projekten verwendet werden kann, sollte er im `/pkg` Verzeichnis liegen. Wenn der Code nicht wiederverwendbar ist oder wenn Sie nicht möchten, dass andere ihn wiederverwenden, setzen Sie diesen Code in das `/internal` Verzeichnis. Sie werden überrascht sein, was andere tun werden, also seien Sie explizit über Ihre Absichten!

Es ist üblich, eine kleine `main` Funktion zu haben, die Code aus den `/internal` und `/pkg` Verzeichnissen importiert und aufruft und nichts anderes.

Beispiele:

* https://github.com/vmware-tanzu/velero/tree/main/cmd (nur eine wirklich kleine `main` Funktion mit allem anderen in Paketen)
* https://github.com/moby/moby/tree/master/cmd
* https://github.com/prometheus/prometheus/tree/main/cmd
* https://github.com/influxdata/influxdb/tree/master/cmd
* https://github.com/kubernetes/kubernetes/tree/master/cmd
* https://github.com/dapr/dapr/tree/master/cmd
* https://github.com/ethereum/go-ethereum/tree/master/cmd
