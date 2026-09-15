
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