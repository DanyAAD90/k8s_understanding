# k8s_understanding
zrozumienie architektury kubernetes

```mermaid
flowchart TD
A[kube api server] --> B[etcd]
C[stan klastra] --> B
A <--> C[kubelet]
subgraph server REST/HTTP
A
end
```
