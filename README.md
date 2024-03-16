# k8s_understanding
zrozumienie architektury kubernetes

```mermaid
flowchart TD
A[kube api server] --> B[etcd]
A <--> C[kubelet]
A --> H[kube-scheduler]
A --> P[kube-controler-manager]
```
```mermaid
flowchart TD
B[etcd] --> D[baza danych key=value]
B --> E[stan wszystkich komponentów]
B --> F[monitoring zadań w klastrze]
B --> G[stan klastra]
```
```mermaid
H[kube-scheduler] --> I[warstwa zarzadzajaca]
H --> J[lokowanie podów do nodów]
H --> K[matrix metryk skomplikowany system decyzyjny]
```
```mermaid
K[matrix metryk skomplikowany system decyzyjny] --> L[dostepnosc zasobów]
K --> M[wymagania aplikacji]
K --> N[manualne reguły mngmt]
K --> O[koszt]
```
```mermaid
P --> R[mngmt grupa wbudowana w klaster]
P --> S[ns,rs,sa,svc node endpoint token job cronjob controllers]
P --> U[ns] --> W[logiczna izolacja obiektow na grupy]
P --> T[mozna dodac wlasne np ingress na L7 secret controler]
```
```mermaid
U --> WA[default nie korzystamy]
U --> WB[kube-system rzadko sie edytuje]
U --> WC[kube-node-lease czas asocjacji z obiektem, leasing time]
U --> WD[kube-public dostepne dla wszystkich]
```
subgraph serwer REST/HTTP
A
end
```
```mermaid
flowchart TD
AA[komponenty WORKER] --> AB[kubelet, odpowiada za pody]
AA --> AC[kube-proxy]
AC --> AD[port-forwarding, modyfikacje FW, ustawianie filtrów]
AA --> AE[CRI container runtime interface] --> AF[CRI-RS runtime service, uruchamianie, zatrzymywanie, usuwanie kontenerów, gRPC]
AE --> AG[CRI-IS image service, pobieranie ładowanie usuwanie obrazów]
AE --> AH[np docker ale sa inne runnery np containerd]
```
```mermaid
flowchart TD
BA[kontener] --> BB[kubelet] --> BC[pod]
BA --> BD[paczka binarna]
BD --> BE[mozna przenosic]
BD --> BF[posiada wbudowane biblioteki]
BD --> BG[posiada wszystkie zaleznosci]
```
```mermaid
flowchart TD
CA[side-car] --> CB[pomagier dla głównych kontenerów]
CA --> CC[SSO sidecar]
CA --> CD[token sidecar] 
```
