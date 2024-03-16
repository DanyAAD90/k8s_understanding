# k8s_understanding
zrozumienie architektury kubernetes

```mermaid
flowchart TD
A[kube api server] --> B[etcd stan klastra]
A <--> C[kubelet]
B --> D[baza danych "key = value"]
B --> E[stan wszystkich komponentów]
B --> F[monitoring zadań w klastrze]

subgraph serwer REST/HTTP
A
end
```
