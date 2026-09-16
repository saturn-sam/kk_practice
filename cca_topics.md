# Cilium Certified Associate (CCA) — Complete Exam Study Guide & Preparation Manual

> **Exam Code:** CCA  
> **Administering Body:** The Linux Foundation & Cloud Native Computing Foundation (CNCF)  
> **Format:** 60 Multiple-Choice Questions (MCQs)  
> **Duration:** 90 Minutes  
> **Passing Score:** 75%  
> **Delivery:** Online Proctored  
> **Target Audience:** DevOps, Platform Engineers, SREs, Kubernetes Operators, and Network Engineers  

---

## Table of Contents

- [Cilium Certified Associate (CCA) — Complete Exam Study Guide \& Preparation Manual](#cilium-certified-associate-cca--complete-exam-study-guide--preparation-manual)
  - [Table of Contents](#table-of-contents)
  - [1. Exam Blueprint \& Domain Weightings](#1-exam-blueprint--domain-weightings)
  - [2. Domain 1: eBPF Fundamentals (10%)](#2-domain-1-ebpf-fundamentals-10)
    - [What is eBPF?](#what-is-ebpf)
    - [Kernel Space vs. User Space](#kernel-space-vs-user-space)
    - [The eBPF Lifecycle: Verification, JIT, Maps, and Tail Calls](#the-ebpf-lifecycle-verification-jit-maps-and-tail-calls)
    - [BPF Hook Points in the Network Stack](#bpf-hook-points-in-the-network-stack)
    - [Why eBPF Replaces iptables and IPVS](#why-ebpf-replaces-iptables-and-ipvs)
      - [The iptables Problem:](#the-iptables-problem)
      - [The IPVS Problem:](#the-ipvs-problem)
      - [The Cilium eBPF Advantage:](#the-cilium-ebpf-advantage)
    - [eBPF Debugging \& Inspection Tools (`bpftool`)](#ebpf-debugging--inspection-tools-bpftool)
  - [3. Domain 2: Cilium Architecture (20%)](#3-domain-2-cilium-architecture-20)
    - [Core Components](#core-components)
    - [Cilium in Kubernetes: Pod Lifecycle \& veth Attachment](#cilium-in-kubernetes-pod-lifecycle--veth-attachment)
    - [Datapath Modes: Encapsulation (Overlay) vs. Native Routing](#datapath-modes-encapsulation-overlay-vs-native-routing)
    - [IP Address Management (IPAM) Modes](#ip-address-management-ipam-modes)
    - [Kube-Proxy Replacement (KPR) \& Socket-Level Load Balancing](#kube-proxy-replacement-kpr--socket-level-load-balancing)
      - [Cilium Kube-Proxy Replacement:](#cilium-kube-proxy-replacement)
      - [KPR Modes:](#kpr-modes)
    - [Load Balancing Modes: SNAT vs. DSR \& Maglev Consistent Hashing](#load-balancing-modes-snat-vs-dsr--maglev-consistent-hashing)
      - [1. SNAT (Source Network Address Translation):](#1-snat-source-network-address-translation)
      - [2. DSR (Direct Server Return):](#2-dsr-direct-server-return)
      - [3. Maglev Consistent Hashing:](#3-maglev-consistent-hashing)
  - [4. Domain 3: Installation \& Configuration (10%)](#4-domain-3-installation--configuration-10)
    - [Installation with Cilium CLI](#installation-with-cilium-cli)
    - [Installation \& Customization with Helm](#installation--customization-with-helm)
    - [Essential Helm Values Explained](#essential-helm-values-explained)
    - [Cluster Connectivity Testing \& Validation](#cluster-connectivity-testing--validation)
    - [Configuration Management \& `cilium-dbg` Inspection](#configuration-management--cilium-dbg-inspection)
    - [Troubleshooting \& Log Collection (`cilium bugtool`)](#troubleshooting--log-collection-cilium-bugtool)
  - [5. Domain 4: Network Policy (18%)](#5-domain-4-network-policy-18)
    - [Kubernetes NetworkPolicy vs. Cilium Network Policy](#kubernetes-networkpolicy-vs-cilium-network-policy)
    - [Policy Enforcement Modes (`default`, `always`, `never`)](#policy-enforcement-modes-default-always-never)
    - [Identity-Based Security Model \& Reserved Identities](#identity-based-security-model--reserved-identities)
      - [The Security Identity Concept:](#the-security-identity-concept)
      - [Reserved Identities:](#reserved-identities)
    - [Layer 3 and Layer 4 Policies](#layer-3-and-layer-4-policies)
    - [Layer 7 Policies (HTTP, gRPC, Kafka)](#layer-7-policies-http-grpc-kafka)
    - [DNS / FQDN-Based Network Policies](#dns--fqdn-based-network-policies)
      - [How Cilium Implements FQDN Policies:](#how-cilium-implements-fqdn-policies)
    - [CiliumClusterwideNetworkPolicy (CCNP) \& Host Firewalls](#ciliumclusterwidenetworkpolicy-ccnp--host-firewalls)
    - [Policy Troubleshooting \& Verdict Inspection](#policy-troubleshooting--verdict-inspection)
  - [6. Domain 5: Service Mesh (16%)](#6-domain-5-service-mesh-16)
    - [Sidecar vs. Sidecarless Service Mesh Architecture](#sidecar-vs-sidecarless-service-mesh-architecture)
      - [Why Sidecarless?](#why-sidecarless)
    - [Cilium Ingress Controller](#cilium-ingress-controller)
    - [Kubernetes Gateway API with Cilium](#kubernetes-gateway-api-with-cilium)
    - [Traffic Management: Canary, URL Rewrite, Header Matching, Mirroring](#traffic-management-canary-url-rewrite-header-matching-mirroring)
    - [Transparent Encryption: WireGuard vs. IPsec](#transparent-encryption-wireguard-vs-ipsec)
      - [1. Configuring WireGuard:](#1-configuring-wireguard)
      - [2. Configuring IPsec:](#2-configuring-ipsec)
    - [Mutual Authentication (mTLS) with SPIFFE / SPIRE](#mutual-authentication-mtls-with-spiffe--spire)
  - [7. Domain 6: Network Observability (10%)](#7-domain-6-network-observability-10)
    - [Hubble Architecture: Hubble Server, Relay, UI, and CLI](#hubble-architecture-hubble-server-relay-ui-and-cli)
    - [Enabling \& Configuring Hubble](#enabling--configuring-hubble)
    - [Flow Types \& Drop Reasons](#flow-types--drop-reasons)
    - [Hubble CLI Syntax \& Practical Filtering Filters](#hubble-cli-syntax--practical-filtering-filters)
    - [Hubble Metrics \& Prometheus/Grafana Export](#hubble-metrics--prometheusgrafana-export)
  - [8. Domain 7: Cluster Mesh (10%)](#8-domain-7-cluster-mesh-10)
    - [Multi-Cluster Connectivity Concepts \& Benefits](#multi-cluster-connectivity-concepts--benefits)
    - [Prerequisites for Cluster Mesh (Critical Exam Topic)](#prerequisites-for-cluster-mesh-critical-exam-topic)
    - [Cluster Mesh Control Plane \& KVStoreMesh](#cluster-mesh-control-plane--kvstoremesh)
    - [Cluster Mesh CLI Setup \& Status Validation](#cluster-mesh-cli-setup--status-validation)
    - [Global Services \& Failover Configurations](#global-services--failover-configurations)
  - [9. Domain 8: BGP \& External Networking (6%)](#9-domain-8-bgp--external-networking-6)
    - [Why BGP in Cloud-Native Networking?](#why-bgp-in-cloud-native-networking)
    - [Cilium BGP Control Plane Architecture](#cilium-bgp-control-plane-architecture)
    - [Cilium BGP CRDs \& Peering Configurations](#cilium-bgp-crds--peering-configurations)
    - [Cilium Egress Gateway (Static Egress IPs)](#cilium-egress-gateway-static-egress-ips)
    - [BPF-Based Bandwidth Manager \& Rate Limiting (EDT)](#bpf-based-bandwidth-manager--rate-limiting-edt)
  - [10. Quick-Recall Exam Cheatsheet (Ports, CLI, Configs)](#10-quick-recall-exam-cheatsheet-ports-cli-configs)
    - [Essential Network Ports](#essential-network-ports)
    - [Key CLI Commands](#key-cli-commands)
  - [11. CCA Practice Exam: 30 Realistic Questions \& Detailed Explanations](#11-cca-practice-exam-30-realistic-questions--detailed-explanations)
    - [Question 1](#question-1)
    - [Question 2](#question-2)
    - [Question 3](#question-3)
    - [Question 4](#question-4)
    - [Question 5](#question-5)
    - [Question 6](#question-6)
    - [Question 7](#question-7)
    - [Question 8](#question-8)
    - [Question 9](#question-9)
    - [Question 10](#question-10)
    - [Question 11](#question-11)
    - [Question 12](#question-12)
    - [Question 13](#question-13)
    - [Question 14](#question-14)
    - [Question 15](#question-15)
    - [Question 16](#question-16)
    - [Question 17](#question-17)
    - [Question 18](#question-18)
    - [Question 19](#question-19)
    - [Question 20](#question-20)
    - [Question 21](#question-21)
    - [Question 22](#question-22)
    - [Question 23](#question-23)
    - [Question 24](#question-24)
    - [Question 25](#question-25)
    - [Question 26](#question-26)
    - [Question 27](#question-27)
    - [Question 28](#question-28)
    - [Question 29](#question-29)
    - [Question 30](#question-30)
  - [Final Review Checklist Before the Exam](#final-review-checklist-before-the-exam)

---

## 1. Exam Blueprint & Domain Weightings

| Domain | Weight | Core Focus Areas |
| :--- | :---: | :--- |
| **Domain 1: Architecture** | **20%** | Cilium Agent, Operator, CNI, Datapath routing modes, IPAM models, KPR |
| **Domain 2: Network Policy** | **18%** | Identities, enforcement modes, CNP vs CCNP, L3/L4/L7/FQDN policies, entities |
| **Domain 3: Service Mesh** | **16%** | Sidecarless architecture, Ingress, Gateway API, WireGuard/IPsec, mTLS with SPIRE |
| **Domain 4: Network Observability**| **10%** | Hubble server, relay, CLI, UI, flow types, drop diagnostics, metrics |
| **Domain 5: Installation & Config**| **10%** | Cilium CLI, Helm values, connectivity testing, `cilium-dbg`, bugtool |
| **Domain 6: Cluster Mesh** | **10%** | Prerequisites, multi-cluster discovery, Global Services, KVStoreMesh |
| **Domain 7: eBPF** | **10%** | Kernel hooks (XDP, TC, sockops), verifier, maps, JIT, iptables vs eBPF |
| **Domain 8: BGP & External Net** | **6%** | BGP Peering, Egress Gateway, BPF Bandwidth Manager (EDT) |

---

## 2. Domain 1: eBPF Fundamentals (10%)

### What is eBPF?
- **eBPF (Extended Berkeley Packet Filter)** is a revolutionary technology that allows running sandboxed user-supplied programs directly inside the Linux kernel without changing kernel source code or loading untrusted kernel modules.
- **Classic BPF (cBPF)** was originally used for simple packet filtering (such as `tcpdump` expressions).
- **eBPF** expanded cBPF into a general-purpose in-kernel virtual machine with 64-bit registers, maps, function calls, and tail calls.

### Kernel Space vs. User Space
```
+-------------------------------------------------------------+
|                        USER SPACE                           |
|  [cilium-agent]    [cilium-operator]    [Hubble Relay / UI] |
|        |                  |                                 |
|        +---- bpftool / LLVM / Clang / libbpf / cilium-dbg  |
+-------------------------------------------------------------+
                            | Syscall (bpf())
+-------------------------------------------------------------+
|                        KERNEL SPACE                         |
|                                                             |
|   +---------------+     +---------------+     +---------+   |
|   |  BPF Verifier | --> |  JIT Compiler | --> | BPF Prog|   |
|   +---------------+     +---------------+     +---------+   |
|                                                    |        |
|   +--------------------------------------------+   |        |
|   |                  BPF Maps                  |<--+        |
|   | (Connections, Endpoints, Identities, IPAM) |            |
|   +--------------------------------------------+            |
|                                                             |
|   Hook Points: [XDP] -> [TC Ingress] -> [Socket] -> [TC Eg] |
+-------------------------------------------------------------+
```

### The eBPF Lifecycle: Verification, JIT, Maps, and Tail Calls
1. **Compilation:** C code is compiled into eBPF bytecode using LLVM/Clang.
2. **Loading:** The user-space daemon loads the bytecode into the kernel via the `bpf()` system call.
3. **BPF Verifier:** Before running any code, the in-kernel verifier guarantees system stability and security:
   - Checks that the program always terminates (bounds loops, prevents infinite loops).
   - Validates memory accesses to prevent reading/writing out-of-bounds or accessing uninitialized memory.
   - Restricts pointer arithmetic.
   - Enforces instruction count limits.
4. **JIT (Just-In-Time) Compiler:** Translates bytecode directly into native machine code (x86_64, ARM64) for bare-metal speed.
5. **BPF Maps:** Generic key-value data structures stored in kernel space. Used for:
   - Sharing state between eBPF programs (e.g., conntrack, endpoint routing table).
   - Bi-directional communication between kernel eBPF programs and user-space daemons (`cilium-agent`).
   - Types: Hash Table, Array, LRU Hash, Ring Buffer, LPM (Longest Prefix Match) Trie.
6. **Tail Calls:** Mechanism allowing an eBPF program to call and transition to another eBPF program without returning to the caller. This allows Cilium to chain modular network logic while staying within kernel instruction limits.

### BPF Hook Points in the Network Stack
Cilium attaches eBPF programs to distinct hooks in the Linux networking subsystem:

| Hook Point | Location | Characteristics | Typical Cilium Use Case |
| :--- | :--- | :--- | :--- |
| **XDP (eXpress Data Path)** | Network driver level (before `sk_buff` memory allocation) | Fastest possible hook; runs before the Linux kernel creates socket buffer packets. | High-speed packet filtering, DDoS mitigation, NodePort load balancing. |
| **TC (Traffic Control - cls_act)** | Ingress and Egress of network interfaces (`veth`, `eth0`, `cilium_vxlan`) | Full access to `sk_buff`, Layer 3/4 header manipulation, packet redirection, encapsulation. | Main Cilium container datapath: routing, network policy enforcement, NAT. |
| **Socket Layer (`sock_ops`, `sk_msg`)** | Socket system calls (`connect`, `sendmsg`, `recvmsg`) inside pod cgroups | Intercepts traffic at the socket layer before packetization into TCP/IP frames. | **Socket-level load balancing (kube-proxy replacement)** and fast pod-to-pod local pipe redirection. |
| **cgroups (`cgroup/sock_addr`)** | Cgroup boundaries of containers/pods | Enforces policies and service IP translation at the moment of the socket creation syscall. | Transparent service IP resolution (`ClusterIP` -> Pod IP) during `connect()`. |
| **kprobes / tracepoints** | Arbitrary kernel function entries / predefined tracepoints | System-level visibility, execution tracking, audit logging. | Runtime security and deep process auditing (used by Cilium Tetragon). |

### Why eBPF Replaces iptables and IPVS

#### The iptables Problem:
- **Sequential $O(N)$ Evaluation:** `iptables` rules are organized in linear lists. Every packet must traverse these rules sequentially until a match is found. In a cluster with 5,000 services (50,000+ rules), packet latency spikes drastically.
- **Global Table Locks (`xtables.lock`):** Any change to a service or endpoint requires a full dump, update, and rewrite of the entire ruleset. This serializes updates, spikes CPU usage, and causes packet drops during frequent pod churn.

#### The IPVS Problem:
- IPVS uses hash tables ($O(1)$ for service lookup), but still relies on iptables for packet filtering, SNAT, and cluster-external routing. It lacks socket-level bypass and Layer 7 context.

#### The Cilium eBPF Advantage:
- **Constant Time $O(1)$ Lookups:** Uses BPF hash maps. Whether you have 10 services or 100,000 endpoints, packet lookup time remains constant.
- **No Global Locking:** Updates to endpoints, services, or policies are performed as atomic single-entry updates to BPF maps in real time without locking the kernel network stack.
- **Kernel Bypass via Sockets:** Translates service IPs at the socket level (`connect()`), bypassing the TCP/IP stack overhead entirely for local communication.

```
+----------------------------------------------------------------------+
|                           PERFORMANCE SCALING                        |
|                                                                      |
|  Latency / Packet Time                                               |
|     ^                                                                |
|     |                                                                |
|     |                              / (iptables: O(N) linear growth)  |
|     |                             /                                  |
|     |                            /                                   |
|     |                           /                                    |
|     |                          /                                     |
|     |                         /                                      |
|     |  -------------------------------- (Cilium eBPF: O(1) constant) |
|     +--------------------------------------------------->            |
|       0                     5,000                     50,000         |
|                          Number of Services / Pods                   |
+----------------------------------------------------------------------+
```

### eBPF Debugging & Inspection Tools (`bpftool`)
`bpftool` is the official utility to inspect and manipulate BPF programs and maps on Linux nodes.

```bash
# Execute bpftool inside the cilium pod
kubectl exec -n kube-system -ti ds/cilium -c cilium-agent -- bpftool prog list

# View active network-attached BPF programs (XDP, TC, cgroup)
kubectl exec -n kube-system -ti ds/cilium -c cilium-agent -- bpftool net show

# Show all loaded BPF maps
kubectl exec -n kube-system -ti ds/cilium -c cilium-agent -- bpftool map show

# Dump the contents of a specific BPF map by ID
kubectl exec -n kube-system -ti ds/cilium -c cilium-agent -- bpftool map dump id <MAP_ID>
```

---

## 3. Domain 2: Cilium Architecture (20%)

### Core Components

```
+--------------------------------------------------------------------------+
|                             KUBERNETES NODE                              |
|                                                                          |
|  +--------------------------------------------------------------------+  |
|  |                  Cilium Agent Pod (DaemonSet)                      |  |
|  |                                                                    |  |
|  |  +----------------+  +-------------------+  +-------------------+  |  |
|  |  |  cilium-agent  |  |    cilium-dbg     |  |   Envoy Proxy     |  |  |
|  |  |  (Go Daemon)   |  |   (Agent CLI)     |  |   (L7 / Mesh)     |  |  |
|  |  +----------------+  +-------------------+  +-------------------+  |  |
|  |          |                     |                      |            |  |
|  |          +------- LLVM / Clang / libbpf Compiles -----+            |  |
|  +--------------------------------------------------------------------+  |
|                                   |                                      |
|  +--------------------------------+-----------------------------------+  |
|  |                           LINUX KERNEL                             |  |
|  |                                                                    |  |
|  |   BPF Maps (Identities, Conntrack, Services, Endpoints, Policies)  |  |
|  |                                                                    |  |
|  |   TC Hook (eth0) <===> TC Hook (cilium_host) <===> TC Hook (veth)  |  |
|  +--------------------------------------------------------------------+  |
|                                   |                                      |
|  +--------------------------------+-----------------------------------+  |
|  |                         APPLICATION PODS                           |  |
|  |   [Pod A (vethXX)]                      [Pod B (vethYY)]           |  |
|  +--------------------------------------------------------------------+  |
+--------------------------------------------------------------------------+
```

1. **Cilium Agent (`cilium-agent`):**
   - Runs as a `DaemonSet` on every Kubernetes worker and control-plane node.
   - Watches the Kubernetes API Server for changes to Pods, Services, NetworkPolicies, and Cilium CRDs.
   - Compiles eBPF programs via LLVM/Clang or loads pre-compiled BPF object files.
   - Writes configuration, routes, and policies into kernel BPF maps.
   - Embeds an **Envoy** instance for Layer 7 traffic routing, Ingress, Gateway API, and service mesh filtering.
2. **Cilium Operator (`cilium-operator`):**
   - Deployed as a centralized `Deployment` (typically 2 replicas with active-standby leader election).
   - Manages non-datapath cluster-wide operations:
     - IP Address Management (IPAM) allocation and CIDR assignment per node.
     - Garbage collection of stale Security Identities and defunct endpoints.
     - Provisioning and managing Cilium Custom Resource Definitions (CRDs).
   - **Critical Exam Concept:** The Cilium Operator is **NOT** in the datapath! If the operator dies or is restarted, existing pods and nodes continue forwarding traffic and enforcing policies without interruption.
3. **Cilium CNI Plugin:**
   - Executed by the container runtime (`containerd` / `CRI-O`) via standard CNI interface upon pod creation/deletion.
   - Configures the virtual ethernet (`veth`) pair connecting the pod network namespace to the host network namespace.
   - Notifies `cilium-agent` to allocate an IP, assign a Security Identity, compile/attach BPF programs, and configure endpoint metadata.
4. **Cilium CLI (`cilium`):**
   - User-facing binary installed on operator/admin workstations.
   - Used for cluster install, upgrade, status verification, connectivity testing, Hubble management, and bug reporting.
5. **`cilium-dbg` (Low-Level Container CLI):**
   - Available inside the `cilium-agent` container (in older versions known as `cilium`).
   - Directly queries and updates local agent state, local BPF maps, endpoints, and identity lists.

### Cilium in Kubernetes: Pod Lifecycle & veth Attachment
When a new Pod is scheduled on a node:
1. Kubelet invokes the Cilium CNI binary via CRI.
2. CNI creates a `veth` pair:
   - One end is placed inside the Pod's network namespace (`eth0`).
   - The other end stays in the host network namespace (`lxcXXXX` or `vethXXXX`).
3. IPAM assigns an IPv4/IPv6 address to the pod.
4. `cilium-agent` allocates or resolves the pod's **Security Identity** based on its K8s labels.
5. Cilium attaches eBPF programs to the host-side `veth` interface using the **TC (Traffic Control)** hook.
6. The pod endpoint is registered in the kernel's BPF endpoint map (`cilium_lxc`).

### Datapath Modes: Encapsulation (Overlay) vs. Native Routing

| Characteristic | Encapsulation / Overlay Mode | Native Routing Mode |
| :--- | :--- | :--- |
| **How it Works** | Pod packets are wrapped in an outer UDP header across the node network. | Pod packets are transmitted as raw IP packets directly onto the physical network. |
| **Protocols** | **VXLAN** (default, UDP port `8472`) or **Geneve** (UDP port `6081`). | Pure L3 routing (Direct Routing, BGP, or Cloud VPC routing). |
| **Network Dependency** | Zero underlying network dependency. Works over any L2/L3 topology or cloud VPC. | Underlying network routers or Cloud VPC route tables must know how to route Pod CIDRs. |
| **MTU Overhead** | Consumes **50 bytes** for VXLAN header (standard 1500 MTU becomes 1450). | No encapsulation header overhead. Full 1500 or 9000 (Jumbo Frame) MTU utilized. |
| **Performance** | Slight CPU cost for encap/decap; slight packet size penalty. | Bare-metal performance; line-rate throughput with minimal CPU overhead. |
| **Visibility** | External packet sniffers see only node-to-node UDP packets. | External firewalls, switches, and IDS/IPS see genuine Pod IPs. |
| **Configuration** | `routingMode: tunnel`<br>`tunnelProtocol: vxlan` | `routingMode: native`<br>`autoDirectNodeRoutes: true` (or BGP) |

### IP Address Management (IPAM) Modes
Cilium supports multiple IPAM architectures:

1. **`cluster-pool` (Default):**
   - The Cilium Operator allocates a sub-pool of IP addresses (e.g., a `/24` CIDR) from a global cluster CIDR to each node.
   - Node-level `cilium-agent` allocates IPs to local pods from this assigned sub-pool.
   - Does not depend on the Kubernetes `node.spec.podCIDR`.
2. **`kubernetes`:**
   - Cilium delegates IPAM to Kubernetes.
   - Kube-controller-manager assigns `podCIDR` to each Node object, and Cilium consumes that exact range.
3. **`azure` / `aws-eni` (Cloud-Provider Native):**
   - Cilium Operator coordinates directly with Cloud APIs.
   - Allocates secondary IP addresses or Elastic Network Interfaces (ENIs) directly to Pods.
   - Every pod receives a real VPC-routable IP address without SNAT.
4. **`crd`:**
   - IP addresses are managed via Cilium-specific `CiliumNode` custom resources.
5. **`multi-pool`:**
   - Enables multiple distinct IP pools within a single cluster. Allows binding specific IP pools to specific nodes, namespaces, or workloads.

### Kube-Proxy Replacement (KPR) & Socket-Level Load Balancing
By default, Kubernetes uses `kube-proxy` to implement Services (`ClusterIP`, `NodePort`, `LoadBalancer`). `kube-proxy` relies on `iptables` or `IPVS`.

#### Cilium Kube-Proxy Replacement:
- Replaces `kube-proxy` entirely by intercepting and redirecting service traffic directly within eBPF.
- **Socket-Level Load Balancing (Client-Side Translation):**
  - When a pod calls `connect()` or `sendmsg()` targeting a `ClusterIP:port`, Cilium's BPF program attached to the cgroup socket hook intercepts the system call.
  - The destination IP:port is rewritten to the chosen backend Pod IP:port **before** the packet is ever formed or sent to the network stack!
  - **Result:** Zero NAT packet overhead, zero iptables traversal, and instant connection establishment.

#### KPR Modes:
- **`strict`:** Complete replacement. `kube-proxy` is uninstalled or completely disabled. All service types (`ClusterIP`, `NodePort`, `LoadBalancer`, `ExternalIPs`, `HostPort`) are implemented by Cilium.
- **`minimal`:** Operates alongside kube-proxy, handling only basic pod-level service traffic.
- **`disabled`:** KPR is disabled; traditional kube-proxy handles all services.

### Load Balancing Modes: SNAT vs. DSR & Maglev Consistent Hashing

#### 1. SNAT (Source Network Address Translation):
- Default NodePort behavior.
- Traffic arriving at Node A for a service whose backend is on Node B has its source IP replaced with Node A's IP so the reply returns to Node A.
- **Drawback:** The backend pod loses the original client IP address (sees Node A's IP).

#### 2. DSR (Direct Server Return):
- The frontend node preserves the original client IP in the packet and encodes the service IP in a custom header.
- The backend pod replies **directly to the client**, completely bypassing the frontend node on the return trip.
- **Benefits:** Retains true client source IP; halves network traffic on intermediate nodes.

#### 3. Maglev Consistent Hashing:
- Consistent hashing algorithm originally developed by Google.
- Ensures packets of the same flow always land on the exact same backend pod even during node or backend churn, without requiring distributed connection state synchronization across nodes.

---

## 4. Domain 3: Installation & Configuration (10%)

### Installation with Cilium CLI
The official Cilium CLI (`cilium`) simplifies operations:

```bash
# 1. Install latest Cilium CLI
CILIUM_CLI_VERSION=$(curl -s https://raw.githubusercontent.com/cilium/cilium-cli/main/stable.txt)
CLI_ARCH=amd64
curl -L --fail --remote-name "https://github.com/cilium/cilium-cli/releases/download/${CILIUM_CLI_VERSION}/cilium-linux-${CLI_ARCH}.tar.gz"
sudo tar xzvfC cilium-linux-${CLI_ARCH}.tar.gz /usr/local/bin
rm cilium-linux-${CLI_ARCH}.tar.gz

# 2. Install Cilium into Kubernetes
cilium install --version 1.15.0

# 3. Verify rollout and status
cilium status --wait
```

### Installation & Customization with Helm
Helm is the production standard for deploying Cilium:

```bash
# Add Cilium Helm repository
helm repo add cilium https://helm.cilium.io/
helm repo update

# Extract default values for reference
helm show values cilium/cilium > values.yaml

# Install Cilium with Kube-Proxy Replacement and Native Routing
helm install cilium cilium/cilium \
  --namespace kube-system \
  --set kubeProxyReplacement=true \
  --set k8sServiceHost="192.168.1.100" \
  --set k8sServicePort="6443" \
  --set routingMode=native \
  --set autoDirectNodeRoutes=true \
  --set ipv4NativeRoutingCIDR="10.244.0.0/16" \
  --set hubble.enabled=true \
  --set hubble.relay.enabled=true \
  --set hubble.ui.enabled=true

# Upgrade Cilium using modified values.yaml
helm upgrade cilium cilium/cilium -n kube-system -f values.yaml

# Restart agents and operator after major configuration changes
kubectl rollout restart -n kube-system deployment/cilium-operator
kubectl rollout restart -n kube-system ds/cilium
```

### Essential Helm Values Explained

```yaml
# Helm values.yaml key parameters
kubeProxyReplacement: true       # Replaces kube-proxy completely
k8sServiceHost: "192.168.1.100"  # Real IP of Kubernetes API Server
k8sServicePort: 6443             # API Server port (required for KPR before agent connects)

routingMode: tunnel              # "tunnel" (encapsulation) or "native"
tunnelProtocol: vxlan            # "vxlan" (port 8472) or "geneve" (port 6081)

ipam:
  mode: cluster-pool             # cluster-pool, kubernetes, aws-eni, azure
  operator:
    clusterPoolIPv4PodCIDRList: ["10.244.0.0/16"]
    clusterPoolIPv4MaskSize: 24

bpf:
  masquerade: true               # Use BPF for IP masquerading instead of iptables

hubble:
  enabled: true                  # Enable local Hubble server inside agent
  relay:
    enabled: true                # Deploy Hubble Relay aggregator
  ui:
    enabled: true                # Deploy Hubble Web Dashboard
```

> **Exam Tip:** When `kubeProxyReplacement=true`, you **MUST** specify `k8sServiceHost` and `k8sServicePort` if the kube-apiserver is not behind an external load balancer. Otherwise, `cilium-agent` cannot discover the API server address because kube-proxy is not running to resolve `kubernetes.default.svc`!

### Cluster Connectivity Testing & Validation
Cilium includes a built-in end-to-end connectivity test framework:

```bash
# Run comprehensive connectivity test suite
cilium connectivity test

# The test suite validates:
# - Pod-to-pod on same node
# - Pod-to-pod across nodes
# - Pod-to-service (ClusterIP, NodePort, HostPort)
# - Pod-to-world (egress internet access)
# - Network policy enforcement (deny-all, L3, L4, L7 HTTP, FQDN)
# - Node-to-node encryption verification
```

### Configuration Management & `cilium-dbg` Inspection
Inside any `cilium` DaemonSet pod, the `cilium-dbg` command provides deep diagnostics:

```bash
# View active agent configuration
kubectl exec -n kube-system ds/cilium -c cilium-agent -- cilium-dbg config view

# Enable real-time debug logging on the fly
kubectl exec -n kube-system ds/cilium -c cilium-agent -- cilium-dbg config set debug true

# Inspect endpoints managed by the local node
kubectl exec -n kube-system ds/cilium -c cilium-agent -- cilium-dbg endpoint list

# View service load-balancing table in BPF
kubectl exec -n kube-system ds/cilium -c cilium-agent -- cilium-dbg service list

# View active BPF connection tracking table
kubectl exec -n kube-system ds/cilium -c cilium-agent -- cilium-dbg bpf ct list global
```

### Troubleshooting & Log Collection (`cilium bugtool`)
When opening issues or performing root-cause analysis:

```bash
# Generate comprehensive debugging archive from all nodes
cilium bugtool

# Gathers:
# - Agent logs and operator logs
# - Kernel dmesg logs
# - BPF maps and program dumps
# - Endpoint statuses and identity tables
# - Network interface stats and IP route tables
```

---

## 5. Domain 4: Network Policy (18%)

### Kubernetes NetworkPolicy vs. Cilium Network Policy

| Feature | Standard K8s NetworkPolicy | CiliumNetworkPolicy (CNP) / CCNP |
| :--- | :---: | :---: |
| **Scope** | Namespace only | Namespace (`CNP`) or Cluster-wide (`CCNP`) |
| **Layer 3 Filtering** | PodSelector, NamespaceSelector, CIDR | PodSelector, Namespace, CIDR, **Entities**, **Nodes** |
| **Layer 4 Filtering** | Port and Protocol (TCP/UDP/SCTP) | Port, Protocol, **Port Ranges** |
| **Layer 7 Filtering** | ❌ Not Supported | ✅ **HTTP (Path/Method), gRPC, Kafka** |
| **DNS / FQDN Rules** | ❌ Not Supported | ✅ **Exact Domain or Wildcard Regex (`*.google.com`)** |
| **Entity Labels** | ❌ Not Supported | ✅ **`world`, `cluster`, `host`, `remote-node`, `health`** |
| **ICMP Rules** | ❌ Not Supported | ✅ **Type and Code Filtering** |
| **Deny Rules** | ❌ Allow-only (implicit deny) | ✅ **Explicit Deny Rules (`deny:`)** |

### Policy Enforcement Modes (`default`, `always`, `never`)
Cilium endpoints have three distinct enforcement modes:
1. **`default` (Whitelist Mode):**
   - If **no policy** selects an endpoint, all ingress and egress traffic is **ALLOWED**.
   - As soon as a policy selects the endpoint for ingress, ingress switches to **default-deny** (only traffic matching allow rules is permitted).
   - Egress remains allowed until an egress policy selects the endpoint.
2. **`always`:**
   - Policy enforcement is **always enabled** on all endpoints.
   - Any endpoint without an explicit policy allowing traffic is immediately in **default-deny**.
3. **`never`:**
   - Policy enforcement is disabled cluster-wide. Packets are always forwarded regardless of any installed NetworkPolicies.

### Identity-Based Security Model & Reserved Identities

#### The Security Identity Concept:
- Cilium does **not** evaluate network policies against volatile, ephemeral IP addresses.
- Instead, Cilium allocates a **Security Identity** (a 32-bit integer) to each unique set of labels.
- If 100 pods share the labels `app=frontend, env=prod`, they all share the exact same Security Identity (e.g., `1045`).
- When Pod A sends a packet to Pod B:
  - Cilium attaches Pod A's Security Identity to the packet metadata (in VXLAN tunnel header or packet mark).
  - The receiving node inspects the identity in the BPF map: `Allow identity 1045 -> identity 2080 on port 80?`.
  - **Lookup complexity:** $O(1)$ instantaneous map lookup.

#### Reserved Identities:

| Identity Name | Numeric Value | Description |
| :--- | :---: | :--- |
| **`host`** | `1` | Traffic originating from or destined to the local node's host network namespace. |
| **`world`** | `2` | Any traffic outside the Kubernetes cluster network (Internet, external networks). |
| **`unmanaged`** | `3` | Pods or interfaces not managed by Cilium (e.g., host-network pods without CNI). |
| **`health`** | `4` | Cilium health monitoring agent (`cilium-health`). |
| **`init`** | `5` | Pods in initialization phase before labels/identities are fully resolved. |
| **`remote-node`** | `6` | Host namespace of any remote node in the cluster (excluding the local host). |
| **`kube-apiserver`**| `7` | Traffic destined to or coming from the Kubernetes API server. |
| **`ingress`** | `8` | Cilium managed Inress / Gateway API Envoy proxies. |

### Layer 3 and Layer 4 Policies

```yaml
apiVersion: "cilium.io/v2"
kind: CiliumNetworkPolicy
metadata:
  name: "secure-backend"
  namespace: "production"
spec:
  endpointSelector:
    matchLabels:
      app: backend
  ingress:
  - fromEndpoints:
    - matchLabels:
        app: frontend
    toPorts:
    - ports:
      - port: "8080"
        protocol: TCP
  egress:
  - toEntities:
    - world
    toPorts:
    - ports:
      - port: "443"
        protocol: TCP
```

### Layer 7 Policies (HTTP, gRPC, Kafka)
When a Layer 7 rule is specified, Cilium's eBPF program redirects the TCP stream to the node's internal **Envoy proxy** for inspection:

```yaml
apiVersion: "cilium.io/v2"
kind: CiliumNetworkPolicy
metadata:
  name: "l7-http-filter"
  namespace: "production"
spec:
  endpointSelector:
    matchLabels:
      app: api-service
  ingress:
  - fromEndpoints:
    - matchLabels:
        app: web-client
    toPorts:
    - ports:
      - port: "80"
        protocol: TCP
      rules:
        http:
        - method: "GET"
          path: "^/public/.*$"
        - method: "POST"
          path: "^/public/upload$"
```
> **Exam Tip:** Any request with method `DELETE` or path `/private/data` will be dropped with an HTTP `403 Forbidden` generated by the Envoy proxy!

### DNS / FQDN-Based Network Policies
Allows pods to securely reach external SaaS services by domain name:

```yaml
apiVersion: "cilium.io/v2"
kind: CiliumNetworkPolicy
metadata:
  name: "allow-github-egress"
  namespace: "production"
spec:
  endpointSelector:
    matchLabels:
      app: ci-builder
  egress:
  # Step 1: Allow DNS traffic to kube-dns so Cilium can intercept responses
  - toEndpoints:
    - matchLabels:
        k8s:io.kubernetes.pod.namespace: kube-system
        k8s-app: kube-dns
    toPorts:
    - ports:
      - port: "53"
        protocol: ANY
      rules:
        dns:
        - matchPattern: "*"
  # Step 2: Allow HTTP/HTTPS traffic only to the resolved IP of the FQDN
  - toFQDNs:
    - matchName: "api.github.com"
    - matchPattern: "*.amazonaws.com"
    toPorts:
    - ports:
      - port: "443"
        protocol: TCP
```

#### How Cilium Implements FQDN Policies:
1. Pod sends DNS request to `kube-dns`.
2. Cilium eBPF redirects the DNS query to an internal Cilium DNS proxy.
3. The DNS proxy observes the IP addresses returned in the DNS `A`/`AAAA` response.
4. Cilium dynamically writes those resolved IPs into a temporary BPF ipcache map associated with that pod's identity.
5. Outbound traffic to those dynamic IPs is permitted until the DNS TTL expires.

### CiliumClusterwideNetworkPolicy (CCNP) & Host Firewalls
- `CiliumClusterwideNetworkPolicy` applies across **all** namespaces.
- Can secure host nodes directly using `nodeSelector`:

```yaml
apiVersion: "cilium.io/v2"
kind: CiliumClusterwideNetworkPolicy
metadata:
  name: "protect-node-ssh"
spec:
  nodeSelector:
    matchLabels:
      kubernetes.io/os: linux
  ingress:
  - fromCIDR:
    - "10.0.0.0/8"
    toPorts:
    - ports:
      - port: "22"
        protocol: TCP
```

### Policy Troubleshooting & Verdict Inspection
```bash
# 1. View policy enforcement status on an endpoint
kubectl exec -n kube-system ds/cilium -c cilium-agent -- cilium-dbg endpoint list

# Look for columns:
# POLICY (INGRESS) -> Enabled / Disabled
# POLICY (EGRESS)  -> Enabled / Disabled

# 2. Stream policy verdicts in real time
kubectl exec -n kube-system ds/cilium -c cilium-agent -- cilium-dbg monitor --type policy-verdict

# 3. Observe dropped packets using Hubble
hubble observe --verdict DROPPED --namespace production
```

---

## 6. Domain 5: Service Mesh (16%)

### Sidecar vs. Sidecarless Service Mesh Architecture

```
TRADITIONAL SIDECAR ARCHITECTURE (Istio, Linkerd classic)
+-----------------------------------------------------------+
| Pod Namespace                                             |
|  [App Container]  <--->  localhost  <--->  [Envoy Sidecar]|
+-----------------------------------------------------------+
       ^                                            |
       | iptables loopback redirection              | TCP Stack
       v                                            v
=============================================================
                      Linux Kernel Stack
=============================================================

CILIUM SIDECARLESS SERVICE MESH
+-----------------------------------------------------------+
| Pod Namespace                                             |
|  [App Container]                                          |
+-----------------------------------------------------------+
       ^
       | eBPF socket redirection (sockops) - zero TCP copy!
       v
+-----------------------------------------------------------+
| Node Host / Cilium Agent                                  |
|  [Single Envoy Instance Per Node] (Only for L7 / Ingress) |
+-----------------------------------------------------------+
```

#### Why Sidecarless?
- **Massive Resource Savings:** Avoids running 1,000 Envoy containers for 1,000 pods (saves gigabytes of RAM).
- **Lower Latency:** L3/L4 traffic never touches Envoy. L7 traffic is redirected directly via eBPF sockops at the socket layer.
- **Simplified Operations:** No pod restarts needed to inject or update proxies.

### Cilium Ingress Controller
Cilium can act as a standard Kubernetes Ingress Controller:

```yaml
# Enable via Helm:
# ingressController.enabled=true
# ingressController.loadbalancerMode=dedicated

apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: web-ingress
  namespace: default
  annotations:
    ingress.class: cilium
spec:
  rules:
  - host: myapp.example.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: web-service
            port:
              number: 80
```

### Kubernetes Gateway API with Cilium
The Gateway API is the modern successor to Ingress:

```yaml
# 1. Gateway definition
apiVersion: gateway.networking.k8s.io/v1
kind: Gateway
metadata:
  name: cilium-gateway
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
        name: tls-cert
        namespace: default
    allowedRoutes:
      namespaces:
        from: All
---
# 2. HTTPRoute definition
apiVersion: gateway.networking.k8s.io/v1
kind: HTTPRoute
metadata:
  name: api-route
  namespace: default
spec:
  parentRefs:
  - name: cilium-gateway
  hostnames:
  - "api.example.com"
  rules:
  - matches:
    - path:
        type: PathPrefix
        value: /v2
    backendRefs:
    - name: api-v2-svc
      port: 8080
  - matches:
    - path:
        type: PathPrefix
        value: /v1
    backendRefs:
    - name: api-v1-svc
      port: 8080
```

### Traffic Management: Canary, URL Rewrite, Header Matching, Mirroring
Gateway API with Cilium supports advanced routing:

```yaml
apiVersion: gateway.networking.k8s.io/v1
kind: HTTPRoute
metadata:
  name: canary-route
  namespace: default
spec:
  parentRefs:
  - name: cilium-gateway
  rules:
  - backendRefs:
    - name: web-service-v1
      port: 80
      weight: 90
    - name: web-service-v2
      port: 80
      weight: 10
```

### Transparent Encryption: WireGuard vs. IPsec

| Feature | WireGuard | IPsec |
| :--- | :--- | :--- |
| **Cryptography** | Modern: ChaCha20-Poly1305, Curve25519 | Traditional: AES-GCM, ESP (RFC 4106) |
| **Key Management** | **Automatic** via `CiliumNode` CRD (Zero manual secret creation). | **Manual** via Kubernetes Secret `cilium-ipsec-keys`. |
| **Hardware Offload** | ❌ No direct crypto NIC offload | ✅ Supported by enterprise NICs |
| **Performance** | High throughput, very low CPU overhead | High, especially if hardware offload enabled |
| **Interface Created**| `cilium_wg0` tunnel interface on node | Managed directly in kernel XFRM subsystem |
| **Node-to-Node Enc** | Supported (`encryption.nodeEncryption=true`) | Supported |
| **Key Rotation** | Automatic | Manual secret update |

#### 1. Configuring WireGuard:
```bash
# Enable in Helm
helm upgrade cilium cilium/cilium -n kube-system \
  --reuse-values \
  --set encryption.enabled=true \
  --set encryption.type=wireguard \
  --set encryption.nodeEncryption=true

# Verify WireGuard encryption status
kubectl exec -n kube-system ds/cilium -c cilium-agent -- cilium-dbg encrypt status
kubectl exec -n kube-system ds/cilium -c cilium-agent -- wg show cilium_wg0
```

#### 2. Configuring IPsec:
```bash
# Step 1: Generate IPsec Pre-Shared Key (PSK) secret
# Format: key-id encryption-algorithm PSK-in-hex key-size
kubectl create -n kube-system secret generic cilium-ipsec-keys \
  --from-literal=keys="3+ rfc4106(gcm(aes)) $(dd if=/dev/urandom count=20 bs=1 2>/dev/null | xxd -p -c 64) 128"

# Step 2: Enable in Helm
helm upgrade cilium cilium/cilium -n kube-system \
  --reuse-values \
  --set encryption.enabled=true \
  --set encryption.type=ipsec

# Step 3: Verify IPsec status
kubectl exec -n kube-system ds/cilium -c cilium-agent -- cilium-dbg encrypt status
```

> **Critical Exam Concept:** Transparent encryption in Cilium encrypts traffic **node-to-node across the network**, not traffic between two pods residing on the exact same worker node!

### Mutual Authentication (mTLS) with SPIFFE / SPIRE
- Traditional mTLS passes all data through an Envoy proxy, increasing CPU usage and latency.
- Cilium implements **mTLS with eBPF data plane separation**:
  1. **Control Plane Handshake:** Cilium delegates identity attestation to **SPIFFE/SPIRE**. SPIRE issues cryptographically verifiable SPIFFE IDs (X.509 SVIDs).
  2. **Mutual Auth Handshake:** An authenticated session is established between nodes.
  3. **eBPF Line-Rate Forwarding:** Once authentication is established, the eBPF datapath forwards packets at line rate without routing through user-space proxies for L3/L4!

---

## 7. Domain 6: Network Observability (10%)

### Hubble Architecture: Hubble Server, Relay, UI, and CLI

```
+-------------------------------------------------------------------------------+
|                            HUBBLE OBSERVABILITY                               |
|                                                                               |
|   +-----------------------+               +-------------------------------+   |
|   |       Hubble UI       |               |          Hubble CLI           |   |
|   |  (Web Dashboard / Map)|               |       (Terminal Client)       |   |
|   +-----------------------+               +-------------------------------+   |
|               \                                       /                       |
|                \                                     /                        |
|                 v                                   v                         |
|   +-----------------------------------------------------------------------+   |
|   |                         Hubble Relay Pod                              |   |
|   |       (Cluster-wide aggregator: Queries all agents via gRPC)          |   |
|   +-----------------------------------------------------------------------+   |
|                                 |                                             |
|        +------------------------+------------------------+                    |
|        | (gRPC: port 4244)                               | (gRPC: port 4244)  |
|        v                                                 v                    |
|   +--------------------------+              +--------------------------+      |
|   | Node 1: Hubble Server    |              | Node 2: Hubble Server    |      |
|   | (Embedded inside cilium) |              | (Embedded inside cilium) |      |
|   +--------------------------+              +--------------------------+      |
|        |                                         |                            |
|   +--------------------------+              +--------------------------+      |
|   | eBPF Perf / Ring Buffer  |              | eBPF Perf / Ring Buffer  |      |
|   +--------------------------+              +--------------------------+      |
+-------------------------------------------------------------------------------+
```

1. **Hubble Server:**
   - Embedded directly into the `cilium-agent` on each node.
   - Reads packet trace events from the eBPF ring buffer with near-zero overhead.
   - Maintains an in-memory ring buffer of recent flows.
2. **Hubble Relay:**
   - Deployed as a centralized service/deployment.
   - Connects to the local Hubble Server on every node over gRPC (port `4244`).
   - Provides a single cluster-wide API endpoint for clients.
3. **Hubble CLI:**
   - Terminal utility that connects to Hubble Relay to query, filter, and stream live flows.
4. **Hubble UI:**
   - Graphical service map showing real-time service-to-service communication dependencies, network flows, and HTTP error rates.

### Enabling & Configuring Hubble
```bash
# Enable Hubble Relay and UI via Cilium CLI
cilium hubble enable --ui

# Verify Hubble components
cilium status

# Establish port-forward to Hubble Relay locally
cilium hubble port-forward&

# Verify connection
hubble status
```

### Flow Types & Drop Reasons
Hubble categorizes network flows:
- **`L3/L4` Flows:** TCP (SYN, FIN, RST, ACK), UDP, ICMP.
- **`L7` Flows:** HTTP (URL, method, status code, latency), DNS (query, answer, TTL), Kafka.
- **Drop Notifications:** When an eBPF program drops a packet:
  - `Policy denied` (blocked by CiliumNetworkPolicy).
  - `CT: Map insertion failed` (connection tracking table full).
  - `Unsupported L3 protocol`.
  - `Encapsulation / Decapsulation error`.

### Hubble CLI Syntax & Practical Filtering Filters

```bash
# Observe all live flows cluster-wide
hubble observe

# Stream live flows continuously
hubble observe --follow

# Filter by Source or Destination Pod
hubble observe --from-pod default/frontend-789 --to-pod default/backend-456

# Filter by Namespace
hubble observe --namespace production

# Filter by Pod Labels
hubble observe --from-label app=frontend --to-label app=backend

# Observe ONLY DROPPED packets (Essential for debugging policy blocks!)
hubble observe --verdict DROPPED

# Filter by Port and Protocol
hubble observe --port 80 --protocol tcp

# Filter Layer 7 HTTP Traffic
hubble observe --http-status 500
hubble observe --http-method POST --http-path "/api/v1/checkout"

# Format output as compact, JSON, or multi-line dict
hubble observe -o compact
hubble observe -o json
```

### Hubble Metrics & Prometheus/Grafana Export
Hubble exports detailed Prometheus metrics configured via Helm:
```yaml
hubble:
  metrics:
    enabled:
    - dns:query;ignoreAAAA
    - drop
    - tcp
    - flow
    - port-distribution
    - httpV2:exemplars=true;labelsContext=source_namespace,source_workload,destination_namespace,destination_workload
```

---

## 8. Domain 7: Cluster Mesh (10%)

### Multi-Cluster Connectivity Concepts & Benefits
Cilium **Cluster Mesh** connects multiple Kubernetes clusters into a single logical network:
- **Pod-to-Pod Direct Routing:** Pods in Cluster 1 can directly connect to Pods in Cluster 2 without ingress controllers or external NAT.
- **Global Services:** Transparent load balancing and automated failover across clusters.
- **Unified Policy Enforcement:** CiliumNetworkPolicies apply seamlessly across cluster boundaries using cluster-aware selectors.

### Prerequisites for Cluster Mesh (Critical Exam Topic)
Before joining clusters into a mesh, you **MUST** ensure:
1. **Unique Cluster Name & ID:** Every cluster must have a unique name and an integer ID between `1` and `255`.
2. **Non-Overlapping PodCIDR and ServiceCIDR:** Pod and Service IP subnets across all participating clusters must not collide.
3. **Matching Datapath / Routing Modes:**
   - If Cluster 1 uses **Encapsulation (VXLAN)**, Cluster 2 **MUST** use Encapsulation (VXLAN).
   - If Cluster 1 uses **Native Routing**, Cluster 2 **MUST** use Native Routing.
4. **Direct Node-to-Node IP Reachability:** Worker nodes in Cluster 1 must have direct IP connectivity to worker nodes in Cluster 2.
5. **Open Network Firewall Ports:**
   - Port `2379` (TCP) for `clustermesh-apiserver` etcd.
   - Port `4240` (TCP) for Cilium health checks.
   - Port `8472` (UDP) for VXLAN (if overlay mode is used).

```
+-----------------------------------+        +-----------------------------------+
|      CLUSTER 1 (ID: 1)            |        |      CLUSTER 2 (ID: 2)            |
|  PodCIDR: 10.0.0.0/16             |        |  PodCIDR: 10.16.0.0/16            |
|  ServiceCIDR: 172.20.0.0/16       |        |  ServiceCIDR: 172.24.0.0/16       |
|                                   |        |                                   |
|  [clustermesh-apiserver] (etcd)   |<======>|  [clustermesh-apiserver] (etcd)   |
|         ^                         |  2379  |         ^                         |
|         |                         |        |         |                         |
|   [cilium-agent]                  |        |   [cilium-agent]                  |
+-----------------------------------+        +-----------------------------------+
        ^                                                    ^
        +================ Direct Pod-to-Pod =================+
```

### Cluster Mesh Control Plane & KVStoreMesh
- **`clustermesh-apiserver`:** Runs an etcd instance in each cluster exposing endpoints, identities, and global services to peer clusters.
- **`KVStoreMesh`:** An intelligent caching proxy layer deployed between clusters in large-scale meshes. Instead of every node connecting to every remote etcd, `KVStoreMesh` caches remote state locally, reducing cross-cluster connections and bandwidth.

### Cluster Mesh CLI Setup & Status Validation
```bash
# Set contexts for both clusters
export CTX1="kind-cluster1"
export CTX2="kind-cluster2"

# 1. Enable Cluster Mesh on Cluster 1
cilium clustermesh enable --context $CTX1 --service-type NodePort

# 2. Enable Cluster Mesh on Cluster 2
cilium clustermesh enable --context $CTX2 --service-type NodePort

# 3. Connect Cluster 1 to Cluster 2
cilium clustermesh connect --context $CTX1 --destination-context $CTX2

# 4. Check Cluster Mesh status and health
cilium clustermesh status --context $CTX1
```

### Global Services & Failover Configurations
A Global Service distributes traffic across backends located in multiple clusters:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: global-database
  namespace: default
  annotations:
    # 1. Mark this service as global across the mesh
    service.cilium.io/global: "true"
    # 2. Shared: endpoints in all clusters actively balance traffic (default: true)
    #    If set to "false", remote endpoints are only used for FAILOVER when local endpoints fail!
    service.cilium.io/shared: "true"
    # 3. Routing affinity: Prefer local cluster endpoints first
    service.cilium.io/affinity: "local"
spec:
  type: ClusterIP
  ports:
  - port: 3306
    targetPort: 3306
  selector:
    app: mysql
```

---

## 9. Domain 8: BGP & External Networking (6%)

### Why BGP in Cloud-Native Networking?
- **Border Gateway Protocol (BGP)** allows Cilium nodes to peer with data center Top-of-Rack (ToR) physical switches or cloud virtual routers.
- **Benefits:**
  - Advertises Pod CIDRs and `Service` (`LoadBalancer` / `ClusterIP`) addresses directly into the physical data center network.
  - Eliminates overlay encapsulation headers.
  - Eliminates ingress hair-pinning and external NAT.
  - Enables Equal-Cost Multi-Path (ECMP) routing for incoming traffic directly to the right nodes.

### Cilium BGP Control Plane Architecture
- Built directly into `cilium-agent` (implemented via GoBGP).
- Enabled via Helm: `bgpControlPlane.enabled=true`.
- Managed declaratively using Kubernetes CRDs.

### Cilium BGP CRDs & Peering Configurations

```yaml
apiVersion: cilium.io/v2alpha1
kind: CiliumBGPPeeringPolicy
metadata:
  name: bgp-peering-tor
spec:
  # Select which Kubernetes nodes will peer via BGP
  nodeSelector:
    matchLabels:
      rack: rack-1
  virtualRouters:
  - localASN: 65001
    exportPodCIDR: true
    neighbors:
    - peerAddress: "192.168.10.1/32"
      peerASN: 65000
      eBGPMultihop: 1
    serviceSelector:
      matchLabels:
        cilium.io/bgp-advertised: "true"
```

### Cilium Egress Gateway (Static Egress IPs)
- **Problem:** Many legacy enterprise systems, payment gateways, and external databases require traffic from Kubernetes to originate from a fixed, whitelisted static IP. By default, pod egress traffic is masqueraded to whichever worker node happens to host the pod.
- **Solution:** `CiliumEgressGatewayPolicy` (CEGP) designates specific nodes as Egress Gateways and SNATs outbound traffic with a dedicated static IP:

```yaml
apiVersion: cilium.io/v2
kind: CiliumEgressGatewayPolicy
metadata:
  name: egress-to-banking-api
spec:
  # Select pods whose egress traffic should be steered
  selectors:
  - podSelector:
      matchLabels:
        app: payment-processor
        io.kubernetes.pod.namespace: production
  # External destination destination CIDR
  destinationCIDRs:
  - "198.51.100.0/24"
  # Designated gateway node that will SNAT the traffic
  egressGateway:
    nodeSelector:
      matchLabels:
        egress-gateway: "true"
    egressIP: "192.168.1.250"
```

### BPF-Based Bandwidth Manager & Rate Limiting (EDT)
- Cilium includes a BPF-based Bandwidth Manager using **EDT (Earliest Departure Time)**.
- Replaces complex Linux HTB/TBF queue disciplines with high-performance eBPF scheduling.
- Enabled via Helm: `bandwidthManager.enabled=true`.
- Pods are rate-limited via standard Kubernetes pod annotations:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: bandwidth-limited-pod
  annotations:
    kubernetes.io/egress-bandwidth: "10M"
    kubernetes.io/ingress-bandwidth: "5M"
spec:
  containers:
  - name: web
    image: nginx
```

---

## 10. Quick-Recall Exam Cheatsheet (Ports, CLI, Configs)

### Essential Network Ports

| Port | Protocol | Purpose |
| :--- | :---: | :--- |
| **`8472`** | UDP | **VXLAN** overlay datapath |
| **`6081`** | UDP | **Geneve** overlay datapath |
| **`4240`** | TCP | Cilium cluster health monitoring (`cilium-health`) |
| **`4244`** | TCP | **Hubble Server** local gRPC listening port inside agent |
| **`4245`** | TCP | **Hubble Relay** cluster-wide gRPC service |
| **`2379`** | TCP | **Cluster Mesh** etcd / `clustermesh-apiserver` |
| **`9878`** | TCP | Cilium Agent Prometheus metrics |
| **`9879`** | TCP | Cilium Operator Prometheus metrics |

### Key CLI Commands

```bash
# Cilium CLI (Workstation tool)
cilium status                         # Cluster deployment health overview
cilium connectivity test              # Run synthetic network & policy verification
cilium hubble enable --ui             # Enable Hubble Relay and UI
cilium hubble port-forward            # Forward local port to Hubble Relay
cilium clustermesh status             # Check multi-cluster peering health
cilium bugtool                        # Export complete debugging archive

# cilium-dbg (Inside cilium pod)
cilium-dbg status                     # Detailed agent & BPF subsystem status
cilium-dbg endpoint list              # List all local endpoints, IDs, and policy states
cilium-dbg identity list              # List Security Identities and label mappings
cilium-dbg service list               # List BPF service load balancing table
cilium-dbg bpf ct list global         # Dump active BPF conntrack table
cilium-dbg encrypt status             # Verify IPsec or WireGuard encryption
cilium-dbg monitor --type drop        # Stream dropped packet events in real time
cilium-dbg config view                # View running agent configuration
cilium-dbg config set debug true      # Toggle debug logging without restart

# Hubble CLI
hubble status                         # Hubble Relay connectivity check
hubble observe                        # Stream live network flows
hubble observe --verdict DROPPED      # View blocked/dropped flows
hubble observe --namespace <ns>       # Filter by namespace
hubble observe --to-pod <pod>         # Filter by destination pod
hubble observe --http-status 500      # Filter by HTTP response code

# bpftool (Kernel inspection inside cilium pod)
bpftool prog list                     # List all loaded kernel eBPF programs
bpftool net show                      # Show BPF programs attached to network devices
bpftool map show                      # List all BPF maps
```

---

## 11. CCA Practice Exam: 30 Realistic Questions & Detailed Explanations

### Question 1
**What happens to active pod network traffic if the `cilium-operator` deployment is scaled to 0 replicas?**
- A) All network traffic across the cluster stops immediately.
- B) Existing network traffic continues to flow and policies remain enforced, but IPAM allocation and identity garbage collection stop.
- C) Pods can communicate locally on the same node, but cross-node traffic is blocked.
- D) eBPF programs are immediately unloaded from the Linux kernel.

> **Answer: B**  
> **Explanation:** The Cilium Operator is strictly in the management/control plane, not in the datapath. Forwarding, routing, and policy enforcement are executed entirely by `cilium-agent` and kernel eBPF programs. If the operator is down, existing datapath traffic is unaffected, though cluster-level management (e.g., allocating new IPAM blocks or garbage collecting stale identities) pauses.

---

### Question 2
**Which Linux kernel hook point does Cilium leverage to implement socket-level load balancing for Kube-Proxy Replacement?**
- A) XDP (eXpress Data Path)
- B) TC (Traffic Control) egress
- C) Socket layer hooks (`sock_ops` / `cgroup/sock_addr`)
- D) Netfilter `PREROUTING`

> **Answer: C**  
> **Explanation:** Cilium attaches eBPF programs to `cgroup` socket hooks (`connect()`, `sendmsg()`). When an application creates a socket and calls `connect()` to a `ClusterIP:port`, Cilium rewrites the destination address to the backend Pod IP:port at the socket layer before packets are generated, bypassing TCP/IP packetization and NAT overhead.

---

### Question 3
**In default policy enforcement mode (`policy-enforcement: default`), what is the behavior for a pod that has NO NetworkPolicies selecting it?**
- A) Ingress and Egress traffic are both blocked (default-deny).
- B) Ingress is allowed, but Egress is blocked.
- C) Ingress and Egress traffic are both allowed (default-allow).
- D) Ingress is blocked, but Egress is allowed.

> **Answer: C**  
> **Explanation:** In `default` mode, an endpoint is in "default-allow" state until at least one policy selects it. Once an Ingress policy selects the endpoint, Ingress enters default-deny while Egress remains default-allow (unless an Egress policy is also created).

---

### Question 4
**How does Cilium assign a Security Identity to an endpoint?**
- A) It hashes the pod's IP address.
- B) It generates an integer based on the pod's metadata labels.
- C) It assigns an integer based on the pod's node name and namespace.
- D) It uses the pod's UID from the Kubernetes API.

> **Answer: B**  
> **Explanation:** Cilium's security model is identity-based, derived strictly from metadata labels (e.g., `app=frontend, env=prod`). Endpoints across the cluster that share identical labels share the exact same numeric Security Identity.

---

### Question 5
**Which of the following is NOT a mandatory prerequisite for enabling Cilium Cluster Mesh?**
- A) Each cluster must have a unique name and a unique Cluster ID between 1 and 255.
- B) PodCIDR and ServiceCIDR must be non-overlapping across all clusters.
- C) All clusters must use the exact same Kubernetes minor version.
- D) Worker nodes must have direct IP connectivity across clusters.

> **Answer: C**  
> **Explanation:** Kubernetes versions do not need to be identical across clusters in a Cluster Mesh. However, unique cluster names/IDs, non-overlapping CIDRs, matching datapath modes, and node IP connectivity are strict prerequisites.

---

### Question 6
**When troubleshooting a dropped packet with the Hubble CLI, which command immediately isolates dropped flows?**
- A) `hubble observe --status error`
- B) `hubble observe --verdict DROPPED`
- C) `hubble flows --type drop`
- D) `hubble monitor --drop`

> **Answer: B**  
> **Explanation:** The flag `--verdict DROPPED` filters live or historical flows to display only packets that were blocked by policy, dropped due to conntrack table exhaustion, or rejected by routing.

---

### Question 7
**Which eBPF hook provides the highest performance for dropping DDoS packets or running Layer 4 NodePort load balancing?**
- A) TC (Traffic Control) ingress
- B) XDP (eXpress Data Path)
- C) Socket sendmsg
- D) kprobe `tcp_v4_rcv`

> **Answer: B**  
> **Explanation:** XDP runs directly at the network interface card (NIC) driver level before the Linux kernel allocates the `sk_buff` (socket buffer) memory structure, making it the fastest possible packet processing hook in Linux.

---

### Question 8
**What is the primary difference between WireGuard and IPsec encryption implementations in Cilium?**
- A) WireGuard requires manual creation of Kubernetes secrets, while IPsec is automatic.
- B) WireGuard automatically manages key generation and exchange via `CiliumNode` CRDs, whereas IPsec requires a manual Kubernetes secret (`cilium-ipsec-keys`).
- C) IPsec creates a `cilium_wg0` interface, while WireGuard operates directly in XFRM.
- D) WireGuard encrypts pod-to-pod traffic on the same node, while IPsec does not.

> **Answer: B**  
> **Explanation:** WireGuard key generation and distribution are fully automated by Cilium via the `CiliumNode` custom resource. IPsec requires administrators to manually create and manage a Kubernetes secret named `cilium-ipsec-keys` containing the encryption key and algorithm specification.

---

### Question 9
**Which Helm setting is MANDATORY when enabling full Kube-Proxy Replacement (`kubeProxyReplacement: true`) without an external API server load balancer?**
- A) `tunnel: geneve`
- B) `k8sServiceHost` and `k8sServicePort`
- C) `autoDirectNodeRoutes: true`
- D) `bpf.masquerade: false`

> **Answer: B**  
> **Explanation:** When kube-proxy is absent, the Cilium agent cannot resolve the `kubernetes.default.svc` ClusterIP during bootstrap. You must explicitly configure `k8sServiceHost` and `k8sServicePort` with the actual IP address and port of the Kubernetes API server so the agent can connect.

---

### Question 10
**What protocol and default port does Cilium use for overlay encapsulation in its default configuration?**
- A) Geneve on UDP 6081
- B) VXLAN on UDP 8472
- C) IPsec on ESP 50
- D) GRE on IP protocol 47

> **Answer: B**  
> **Explanation:** Cilium defaults to VXLAN encapsulation running over UDP port `8472`.

---

### Question 11
**You have a pod running in namespace `production`. You apply a `CiliumNetworkPolicy` that specifies an `ingress` rule permitting traffic from `app: frontend` on port `80`. What happens to egress traffic from this pod?**
- A) Egress traffic is immediately blocked because the pod is now selected by a policy.
- B) Egress traffic remains completely allowed because no egress rules have selected the pod.
- C) Egress traffic is restricted to port 80 only.
- D) Egress traffic is redirected to the Envoy proxy.

> **Answer: B**  
> **Explanation:** In Cilium, Ingress and Egress policy enforcement are tracked independently. Applying an Ingress-only policy puts the pod into default-deny for Ingress, but Egress remains in default-allow until an Egress rule selects the pod.

---

### Question 12
**What is the purpose of the `cilium bugtool` utility?**
- A) It fixes kernel verifier errors automatically.
- B) It compiles BPF source files into bytecode.
- C) It gathers comprehensive diagnostics, logs, BPF map states, and routing tables into a compressed tarball for troubleshooting.
- D) It runs synthetic HTTP latency tests against endpoints.

> **Answer: C**  
> **Explanation:** `cilium bugtool` is the standard diagnostic gathering tool that extracts system information, kernel logs, agent logs, and BPF maps to assist in troubleshooting.

---

### Question 13
**Which Cilium service mesh feature allows splitting traffic between two different backend services (90% to v1 and 10% to v2)?**
- A) CiliumClusterwideNetworkPolicy
- B) Kubernetes Gateway API with `HTTPRoute` weights
- C) Cilium BGP Peering Policy
- D) `cilium-dbg service update`

> **Answer: B**  
> **Explanation:** Using the Kubernetes Gateway API with an `HTTPRoute`, you can specify multiple `backendRefs` with respective `weight` values (e.g., weight 90 and weight 10) to achieve canary traffic splitting.

---

### Question 14
**Which reserved identity is assigned to traffic originating from the local host node's network namespace?**
- A) `world`
- B) `remote-node`
- C) `host`
- D) `unmanaged`

> **Answer: C**  
> **Explanation:** The reserved identity `host` (numeric value `1`) represents the local host network namespace on the node.

---

### Question 15
**What is the key advantage of Direct Server Return (DSR) compared to standard SNAT for NodePort traffic?**
- A) DSR eliminates the need for BPF programs.
- B) DSR preserves the client source IP and routes response packets directly from the backend node back to the client, bypassing the entry node.
- C) DSR encrypts all traffic using IPsec automatically.
- D) DSR works over any overlay without MTU considerations.

> **Answer: B**  
> **Explanation:** Under standard SNAT, the entry node rewrites the client IP to its own IP, causing response traffic to hairpin through the entry node and obscuring client identity. DSR preserves the client source IP and enables the backend node to reply directly to the client.

---

### Question 16
**When configuring DNS/FQDN-based network policies in Cilium, why must the policy also allow access to `kube-dns` on UDP/TCP port 53?**
- A) To allow kube-dns to look up Cilium endpoints.
- B) So Cilium's internal DNS proxy can intercept the DNS response and learn the dynamic IP addresses mapped to the FQDN.
- C) Because FQDN rules are evaluated inside kube-dns.
- D) To update Kubernetes CoreDNS ConfigMaps.

> **Answer: B**  
> **Explanation:** Cilium does not perform independent polling of external domains. Instead, it intercepts the pod's actual DNS queries and responses to CoreDNS via an internal DNS proxy. It parses the response IPs and injects them into the pod's BPF allow list.

---

### Question 17
**What CLI tool inside the `cilium` container is used to directly inspect local endpoints and BPF maps?**
- A) `kubectl`
- B) `cilium-dbg`
- C) `hubble-relay`
- D) `kube-proxy`

> **Answer: B**  
> **Explanation:** `cilium-dbg` is the administrative tool located inside the `cilium` container (symlinked to `cilium` in older versions) that communicates directly with the local agent daemon via a Unix domain socket.

---

### Question 18
**Which of the following annotations makes a standard Kubernetes Service available across all connected clusters in a Cilium Cluster Mesh?**
- A) `service.cilium.io/mesh: "enabled"`
- B) `service.cilium.io/global: "true"`
- C) `clustermesh.cilium.io/replicated: "true"`
- D) `io.cilium/multi-cluster: "yes"`

> **Answer: B**  
> **Explanation:** The annotation `service.cilium.io/global: "true"` instructs Cilium to advertise service endpoints across all clusters joined in the mesh.

---

### Question 19
**In Cilium's Sidecarless Service Mesh, where is Layer 7 policy enforcement and TLS termination processed?**
- A) In the kernel BPF verifier.
- B) In a sidecar Envoy container injected into every application pod.
- C) In an Envoy proxy instance managed by the Cilium Agent at the node level.
- D) In the Kubernetes API Server.

> **Answer: C**  
> **Explanation:** Cilium's sidecarless architecture runs an Envoy instance embedded in or managed by `cilium-agent` on each node. Traffic requiring L7 inspection is forwarded to this node-level proxy via eBPF sockops.

---

### Question 20
**What does the BPF Verifier do when an eBPF program contains an unbounded loop?**
- A) It runs the loop until 1,000 iterations and then terminates it.
- B) It compiles the loop into a recursive tail call.
- C) It rejects the program at load time to prevent kernel freezes or deadlocks.
- D) It offloads the loop execution to user space.

> **Answer: C**  
> **Explanation:** The BPF verifier performs static analysis before loading bytecode. Unbounded loops or potential infinite loops are strictly rejected to ensure the program cannot crash or freeze the Linux kernel.

---

### Question 21
**What is the function of `KVStoreMesh` in large-scale Cilium Cluster Mesh deployments?**
- A) It synchronizes container images across clusters.
- B) It acts as a caching proxy that reduces the number of cross-cluster etcd connections between nodes.
- C) It replaces BGP routers in physical networks.
- D) It automatically rotates WireGuard encryption keys.

> **Answer: B**  
> **Explanation:** In large meshes, having every `cilium-agent` connect to every remote cluster's etcd creates an $N \times M$ connection explosion. `KVStoreMesh` runs as a caching proxy to optimize and aggregate cross-cluster state synchronization.

---

### Question 22
**Which IPAM mode should you select if you want pods to receive native, routable IP addresses directly from an AWS VPC subnet without SNAT?**
- A) `cluster-pool`
- B) `kubernetes`
- C) `aws-eni`
- D) `crd`

> **Answer: C**  
> **Explanation:** In `aws-eni` IPAM mode, the Cilium Operator interacts directly with the AWS EC2 API to allocate secondary IPs and ENIs to nodes, giving pods genuine VPC-routable IP addresses.

---

### Question 23
**Which Cilium custom resource is used to route outbound pod traffic through a designated gateway node with a predictable static IP address?**
- A) `CiliumBGPPeeringPolicy`
- B) `CiliumEgressGatewayPolicy`
- C) `CiliumClusterwideNetworkPolicy`
- D) `CiliumNodeConfig`

> **Answer: B**  
> **Explanation:** A `CiliumEgressGatewayPolicy` (CEGP) steers egress traffic matching specific pod/destination selectors to an egress gateway node that SNATs the packets with a dedicated static IP.

---

### Question 24
**How does Cilium achieve Mutual Authentication (mTLS) without suffering the high CPU and latency overhead of traditional proxy-based service meshes?**
- A) It hardcodes TLS certificates into eBPF maps.
- B) It separates the authentication handshake (delegated to SPIFFE/SPIRE) from the datapath, allowing eBPF to forward verified traffic at line rate.
- C) It disables encryption and uses plaintext security tokens.
- D) It relies on Linux user-space iptables tunnels.

> **Answer: B**  
> **Explanation:** Cilium decouples the authentication control plane from the data plane. SPIFFE/SPIRE performs mutual attestation and issues certificates, while the eBPF datapath validates that an authenticated connection is active and forwards packets at bare-metal line rate.

---

### Question 25
**What command allows you to view the currently configured routing mode and BPF settings in a running Cilium agent?**
- A) `cilium-dbg config view`
- B) `hubble status --config`
- C) `bpftool config show`
- D) `cilium-operator status`

> **Answer: A**  
> **Explanation:** `cilium-dbg config view` prints all active configuration flags, routing modes, and BPF features enabled on the local node's agent.

---

### Question 26
**What is the maximum integer value allowed for a Cluster ID when configuring Cilium Cluster Mesh?**
- A) 16
- B) 255
- C) 1024
- D) 65535

> **Answer: B**  
> **Explanation:** In Cilium Cluster Mesh, Cluster IDs must be unique integers between `1` and `255` (allocated within an 8-bit field in packet metadata/identity allocation).

---

### Question 27
**If you want to enforce network policies across all namespaces in a cluster without duplicating manifests in each namespace, which resource must you use?**
- A) `NetworkPolicy`
- B) `CiliumNetworkPolicy`
- C) `CiliumClusterwideNetworkPolicy`
- D) `CiliumGlobalPolicy`

> **Answer: C**  
> **Explanation:** `CiliumClusterwideNetworkPolicy` (CCNP) is a non-namespaced cluster-scoped resource that applies policy rules across all namespaces or against cluster nodes.

---

### Question 28
**Which Hubble component connects to individual node agents to provide a unified cluster-wide API for the Hubble CLI and UI?**
- A) Hubble Agent
- B) Hubble Relay
- C) Hubble Ingress
- D) Hubble Verifier

> **Answer: B**  
> **Explanation:** Hubble Relay acts as a gRPC aggregator. It connects to the Hubble servers on every individual node (over port 4244) and presents a single, cluster-wide flow API on port 4245.

---

### Question 29
**What is the impact of configuring `autoDirectNodeRoutes: true` in native routing mode when all nodes share a common Layer 2 broadcast domain?**
- A) Cilium sets up VXLAN tunnels between nodes.
- B) Cilium configures direct kernel routing table entries on each node for every other node's PodCIDR, avoiding the need for BGP.
- C) Cilium disables eBPF and falls back to Linux bridging.
- D) Cilium assigns public IP addresses to all pods.

> **Answer: B**  
> **Explanation:** When nodes are on the same L2 subnet, `autoDirectNodeRoutes: true` configures host routing entries pointing to peer nodes as next-hops for their respective Pod CIDRs, enabling direct native routing without a BGP daemon or overlay encapsulation.

---

### Question 30
**Which command is used to stream live dropped network packets directly on a node using Cilium's low-level monitor?**
- A) `cilium-dbg monitor --type drop`
- B) `bpftool monitor drop`
- C) `hubble filter --drop`
- D) `tcpdump -i any drop`

> **Answer: A**  
> **Explanation:** `cilium-dbg monitor --type drop` taps into the agent's internal BPF notification ring buffer and prints dropped packet events with reason codes in real time.

---

## Final Review Checklist Before the Exam

- [ ] Can explain how eBPF works (Verifier $\rightarrow$ JIT $\rightarrow$ Maps $\rightarrow$ Tail Calls).
- [ ] Understand XDP vs. TC vs. Socket hook points.
- [ ] Understand why iptables $O(N)$ fails at scale compared to eBPF $O(1)$.
- [ ] Understand Cilium Agent vs. Operator responsibilities (and why Operator is not in datapath).
- [ ] Know the difference between Encapsulation (VXLAN/Geneve) and Native Routing.
- [ ] Master Kube-Proxy Replacement: Socket-level load balancing and why it avoids NAT overhead.
- [ ] Understand Identity-Based Security: labels $\rightarrow$ numeric identity; reserved identities (`host`, `world`, `remote-node`, `health`).
- [ ] Know CNP vs. CCNP vs. K8s NetworkPolicy.
- [ ] Write and read L3, L4, L7 (HTTP/gRPC/Kafka), and DNS/FQDN policy rules.
- [ ] Differentiate WireGuard (automatic key exchange, `cilium_wg0`) from IPsec (manual K8s secret).
- [ ] Explain Sidecarless Service Mesh advantages (resource efficiency, socket redirection, node Envoy).
- [ ] Master Hubble CLI commands (`hubble observe --verdict DROPPED`, filtering by pod, namespace, HTTP).
- [ ] Know all Cluster Mesh prerequisites (Unique Name & ID 1-255, non-overlapping CIDRs, matching datapath).
- [ ] Know Global Service annotations (`service.cilium.io/global`, `shared`, `affinity`).
- [ ] Understand BGP peering role and Egress Gateway (`CiliumEgressGatewayPolicy`).
- [ ] Memorize ports: `8472` (VXLAN), `4240` (Health), `4244` (Hubble Server), `4245` (Hubble Relay), `2379` (Cluster Mesh).

