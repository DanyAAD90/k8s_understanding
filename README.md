# k8s_understanding
zrozumienie architektury kubernetes

```mermaid
flowchart TD
A[kube api server] --> B[etcd]
A <--> C[kubelet]
B --> D[baza danych key=value]
B --> E[stan wszystkich komponentów]
B --> F[monitoring zadań w klastrze]
B --> G[stan klastra]
A --> H[kube-scheduler]
H --> I[warstwa zarzadzajaca]
H --> J[lokowanie podów do nodów]
H --> K[matrix metryk skomplikowany system decyzyjny]
K --> L[dostepnosc zasobów]
K --> M[wymagania aplikacji]
K --> N[manualne reguły mngmt]
K --> O[koszt]
A --> P[kube-controler-manager]
P --> R[mngmt grupa wbudowana w klaster]
P --> S[ns,rs,sa itp controllers]
subgraph serwer REST/HTTP
A
end
```
