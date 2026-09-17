
cilium has 2 routing mode
1. Encapsulation
2. Native routing

usage of bpftool

`k exec cilium-agen -n kube-system -- bpftool net show`

2 useful cilium command-

1. `cilium config view`
2. `cilium config set debug true`

net testing image-

`nicolaca/netshoot`


helm value extract and upgrade

```
helm show values cilium/cilium > values.yaml

helm upgrade cilium cilium/cilium -n kube-system -f values.yaml

# rollout restart service-

k rollout restart -n kube-system deployment/cilium-operator

k rollout restart -n kube-system ds/cilium

```

gateway example-

```
apiVersion: gateway.networking.k8s.io/v1
kind: Gateway
metadata:
  name: my-gateway
  namespace: default
spec:
  gatewayClassName: cilium
  listeners:
  - name: http
    protocol: HTTP
    port: 80
    allowedRoutes:
      namespaces:
        from: Same
  - name: https
    protocol: HTTPS
    port: 443
    tls:
      mode: Terminate
      certificateRefs:
      - kind: Secret
        name: my-cert
        namespace: default
    allowedRoutes:
      namespaces:
        from: Same
```

Encryption

1. ipsec
2. wireguard

encryption secret-

`key-id encryption-algorithm PSK-in-hex-format key-size`

```
$ kubectl create -n kube-system secret generic cilium-ipsec-keys \
    --from-literal=keys="3+ rfc4106(gcm(aes)) $(echo $(dd if=/dev/urandom count=20 bs=1 2> /dev/null | xxd -p -c 64)) 128"
```

to enable encryption need to edit helm values-

```
encryption:
    enabled: true
    type: ipsec #other is wireguard
```

varify cilium encryption -

```
cilium-dbg encrypt status
```

this encryption encript trffic of pods of node to node, not within same node.


mTLS

>Cilium uses spifee (framework for secure identity management) and implemented by spire (open-source implementation of spifee)

Cluster mesh prereq

1. matching data path mode across cluster
    ie. if 1 cluster is native-routing mode then all cluster should be native-routing mode and if 1 cluster is encapsulation mode then all cluster should be encapsulation mode

2. non-overlapping pod cidr
3. full node to node ip connectivity


```bash
cilium clustermesh enable --context $CLUSTER1

cilium clustermesh connect --contect $CLUSTER1 --destination-context $CLUSTER2

cilium clustermesh status
```

KVStoreMesh

Cilium uses a shared key-value store to help clusters discover and sync network information, so multi-cluster communication works smoothly.


command deploys the Cilium CLI connectivity test pod, verifying both node-to-node and pod-to-pod networking and DNS resolution?

`cilium connectivity test`


You want to inspect the full current configuration as seen by the Cilium agent (including values from the ConfigMap, CLI flags, and environment variables), regardless of how they were set, on a specific node. Which Cilium CLI command achieves this?

`cilium cli config view`

need study on-
- gateway api


86%
Network Policy

25%
Installation & Configuration

67%
Enabling Layer-7 Protocol Visibility

50%
Kubernetes Network Policies versus Cilium Network Policies

50%
Policy Enforcement Modes

67%
Understand the Benefits of Gateway API Over Ingress

50%
IP Address Management (IPAM) with Cilium

33%
Service Mesh