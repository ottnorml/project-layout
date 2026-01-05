# `/pkg`

Bibliothekscode, der von externen Anwendungen verwendet werden darf (z.B. `/pkg/mypubliclib`). Andere Projekte werden diese Bibliotheken importieren und erwarten, dass sie funktionieren, also denken Sie zweimal nach, bevor Sie etwas hier ablegen :-) Beachten Sie, dass das `internal` Verzeichnis ein besserer Weg ist, um sicherzustellen, dass Ihre privaten Pakete nicht importierbar sind, weil es von Go erzwungen wird. Das `/pkg` Verzeichnis ist immer noch ein guter Weg, um explizit zu kommunizieren, dass der Code in diesem Verzeichnis sicher von anderen verwendet werden kann. Der [`I'll take pkg over internal`](https://travisjeffery.com/b/2019/11/i-ll-take-pkg-over-internal/) Blogbeitrag von Travis Jeffery bietet einen guten Überblick über die `pkg` und `internal` Verzeichnisse und wann es sinnvoll sein könnte, sie zu verwenden.

Es ist auch eine Möglichkeit, Go-Code an einem Ort zu gruppieren, wenn Ihr Root-Verzeichnis viele Nicht-Go-Komponenten und Verzeichnisse enthält, was es einfacher macht, verschiedene Go-Tools auszuführen (wie in diesen Vorträgen erwähnt: [`Best Practices for Industrial Programming`](https://www.youtube.com/watch?v=PTE4VJIdHPg) von GopherCon EU 2018, [GopherCon 2018: Kat Zien - How Do You Structure Your Go Apps](https://www.youtube.com/watch?v=oL6JBUk6tj0) und [GoLab 2018 - Massimiliano Pippi - Project layout patterns in Go](https://www.youtube.com/watch?v=3gQa1LWwuzk)).

Beachten Sie, dass dies kein universell akzeptiertes Muster ist und für jedes beliebte Repo, das es verwendet, finden Sie 10, die es nicht tun. Es liegt an Ihnen zu entscheiden, ob Sie dieses Muster verwenden möchten oder nicht. Unabhängig davon, ob es ein gutes Muster ist oder nicht, werden mehr Leute wissen, was Sie meinen, als nicht. Es könnte für einige der neuen Go-Entwickler etwas verwirrend sein, aber es ist eine ziemlich einfache Verwirrung zu lösen, und das ist eines der Ziele für dieses Projektlayout-Repo.

Es ist in Ordnung, es nicht zu verwenden, wenn Ihr App-Projekt wirklich klein ist und eine zusätzliche Verschachtelungsebene nicht viel Wert hinzufügt (es sei denn, Sie möchten es wirklich). Denken Sie darüber nach, wenn es groß genug wird und Ihr Root-Verzeichnis ziemlich voll wird (besonders wenn Sie viele Nicht-Go-App-Komponenten haben).

Die Ursprünge des `pkg` Verzeichnisses: Der alte Go-Quellcode verwendete `pkg` für seine Pakete und dann begannen verschiedene Go-Projekte in der Community, das Muster zu kopieren (siehe [`diesen`](https://twitter.com/bradfitz/status/1039512487538970624) Tweet von Brad Fitzpatrick für mehr Kontext).


Beispiele:

* https://github.com/containerd/containerd/tree/main/pkg
* https://github.com/slimtoolkit/slim/tree/master/pkg
* https://github.com/telepresenceio/telepresence/tree/release/v2/pkg
* https://github.com/jaegertracing/jaeger/tree/master/pkg
* https://github.com/istio/istio/tree/master/pkg
* https://github.com/GoogleContainerTools/kaniko/tree/master/pkg
* https://github.com/google/gvisor/tree/master/pkg
* https://github.com/google/syzkaller/tree/master/pkg
* https://github.com/perkeep/perkeep/tree/master/pkg
* https://github.com/heptio/ark/tree/master/pkg
* https://github.com/argoproj/argo-workflows/tree/master/pkg
* https://github.com/argoproj/argo-cd/tree/master/pkg
* https://github.com/heptio/sonobuoy/tree/master/pkg
* https://github.com/helm/helm/tree/master/pkg
* https://github.com/k3s-io/k3s/tree/master/pkg
* https://github.com/kubernetes/kubernetes/tree/master/pkg
* https://github.com/kubernetes/kops/tree/master/pkg
* https://github.com/moby/moby/tree/master/pkg
* https://github.com/grafana/grafana/tree/master/pkg
* https://github.com/influxdata/influxdb/tree/master/pkg
* https://github.com/cockroachdb/cockroach/tree/master/pkg
* https://github.com/derekparker/delve/tree/master/pkg
* https://github.com/etcd-io/etcd/tree/master/pkg
* https://github.com/oklog/oklog/tree/master/pkg
* https://github.com/flynn/flynn/tree/master/pkg
* https://github.com/jesseduffield/lazygit/tree/master/pkg
* https://github.com/gopasspw/gopass/tree/master/pkg
* https://github.com/sosedoff/pgweb/tree/master/pkg
* https://github.com/GoogleContainerTools/skaffold/tree/master/pkg
* https://github.com/knative/serving/tree/master/pkg
* https://github.com/grafana/loki/tree/master/pkg
* https://github.com/bloomberg/goldpinger/tree/master/pkg
* https://github.com/Ne0nd0g/merlin/tree/master/pkg
* https://github.com/jenkins-x/jx/tree/master/pkg
* https://github.com/DataDog/datadog-agent/tree/master/pkg
* https://github.com/dapr/dapr/tree/master/pkg
* https://github.com/cortexproject/cortex/tree/master/pkg
* https://github.com/dexidp/dex/tree/master/pkg
* https://github.com/pusher/oauth2_proxy/tree/master/pkg
* https://github.com/pdfcpu/pdfcpu/tree/master/pkg
* https://github.com/weaveworks/kured/tree/master/pkg
* https://github.com/weaveworks/footloose/tree/master/pkg
* https://github.com/weaveworks/ignite/tree/master/pkg
* https://github.com/tmrts/boilr/tree/master/pkg
* https://github.com/kata-containers/runtime/tree/master/pkg
* https://github.com/okteto/okteto/tree/master/pkg
* https://github.com/solo-io/squash/tree/master/pkg
* https://github.com/google/exposure-notifications-server/tree/main/pkg
* https://github.com/spiffe/spire/tree/main/pkg
* https://github.com/rook/rook/tree/master/pkg
* https://github.com/buildpacks/pack/tree/main/pkg
* https://github.com/cilium/cilium/tree/main/pkg
* https://github.com/containernetworking/cni/tree/main/pkg
* https://github.com/crossplane/crossplane/tree/master/pkg
* https://github.com/dragonflyoss/Dragonfly2/tree/main/pkg
* https://github.com/kubeedge/kubeedge/tree/master/pkg
* https://github.com/kubevela/kubevela/tree/master/pkg
* https://github.com/kubevirt/kubevirt/tree/main/pkg
* https://github.com/kyverno/kyverno/tree/main/pkg
* https://github.com/thanos-io/thanos/tree/main/pkg
* https://github.com/cri-o/cri-o/tree/main/pkg
* https://github.com/fluxcd/flux2/tree/main/pkg
* https://github.com/kedacore/keda/tree/main/pkg
* https://github.com/linkerd/linkerd2/tree/main/pkg
* https://github.com/opencost/opencost/tree/develop/pkg
* https://github.com/antrea-io/antrea/tree/main/pkg
* https://github.com/karmada-io/karmada/tree/master/pkg
* https://github.com/kuberhealthy/kuberhealthy/tree/master/pkg
* https://github.com/submariner-io/submariner/tree/devel/pkg
* https://github.com/trickstercache/trickster/tree/main/pkg
* https://github.com/tellerops/teller/tree/master/pkg
* https://github.com/OpenFunction/OpenFunction/tree/main/pkg
* https://github.com/external-secrets/external-secrets/tree/main/pkg
* https://github.com/ko-build/ko/tree/main/pkg
* https://github.com/lima-vm/lima/tree/master/pkg
* https://github.com/clastix/capsule/tree/master/pkg
* https://github.com/carvel-dev/ytt/tree/develop/pkg
* https://github.com/clusternet/clusternet/tree/main/pkg
* https://github.com/fluid-cloudnative/fluid/tree/master/pkg
* https://github.com/inspektor-gadget/inspektor-gadget/tree/main/pkg
* https://github.com/sustainable-computing-io/kepler/tree/main/pkg
* https://github.com/GoogleContainerTools/kpt/tree/main/pkg
* https://github.com/guacsec/guac/tree/main/pkg
* https://github.com/kubeovn/kube-ovn/tree/master/pkg
* https://github.com/kube-vip/kube-vip/tree/main/pkg
* https://github.com/kubescape/kubescape/tree/master/pkg
* https://github.com/kudobuilder/kudo/tree/main/pkg
* https://github.com/kumahq/kuma/tree/master/pkg
* https://github.com/kubereboot/kured/tree/main/pkg
* https://github.com/nocalhost/nocalhost/tree/main/pkg
* https://github.com/openelb/openelb/tree/master/pkg
* https://github.com/openfga/openfga/tree/main/pkg
* https://github.com/openyurtio/openyurt/tree/master/pkg
* https://github.com/getporter/porter/tree/main/pkg
* https://github.com/sealerio/sealer/tree/main/pkg
* https://github.com/werf/werf/tree/main/pkg
  
