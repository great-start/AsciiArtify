## Characteristics

### Minikube

`Supported OS and Arch:` Windows, macOS, та Linux. Architectures: x86-64, arm64, armv7, ppc64, s390x
`Automation Capability:` Offers automation for cluster creation and management. But poor automation options - no configuration file set up a whole cluster as specified.
`Additional Features:`

- Suitable for local development and testing.
- Multiple logical clusters on one dev machine (minikube profiles are logical clusters that can be started and stopped separately from each other)
- Has integrated support for the Kubernetes Dashboard UI.
- Ability to use all K8s features with minikube (Addons)

### Kind (Kubernetes IN Docker)

`Supported OS and Arch:` Linux, macOS and Windows. Works within Docker containers.
`Automation Capability:` Allows the creation of local Kubernetes clusters in Docker containers.
`Additional Features:`

- Suitable for local development and testing.
- Provides a cluster configuration file
- Provide feature gates to enable experimental Kubernetes features and plenty of other configuration options.

### k3d

`Supported OS and Arch:` Linux, macOS and Windows. Uses Rancher Kubernetes Engine (RKE) in Docker containers.
`Automation Capability:` Facilitates quick creation and testing of Kubernetes clusters in Docker containers.
`Additional Features:`

- Suitable for local development and testing.
- Simple installation
- Provides a cluster configuration file
- Chosen for preparing Proof of Concept (PoC).

### Proc & conc

|          | **Minikube**                                                                                                                                  | **Kind**                                                                                                                                         | **k3d**                                                                                                                                                                        |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Pros** | - Easy to use<br> - Suitable for local development and testing<br> - Build-in Bashboard UI<br> - A lot of options for customizing the cluster | - Suitable for local development and testing<br>- Works within Docker containers<br>- Possibility for local testing<br>- Poor automation options | - Suitable for local development and testing<br>- Works within Docker containers<br>- Fast cluster creation and testing<br>- Solid Podman support<br>- Consumes less resources |
| **Cons** | - Doubts about scalability<br>- Potential limitations<br>- Some restriction in Container runtime, podman support (experimental)               | - Limited information on scalability<br>- Limited community documentation                                                                        | - Limited documentation<br>- Potential scalability concerns                                                                                                                    |

## Demonstration

Recommendation: k3d

![Application on Kubernetes](123456.gif)
