# Kubernetes azure-cloud-controller-manager

## Notice
This repository provides tools and scripts for building and testing `Kubernetes cloud-controller-manager` for Azure. The project is under development.

The azure cloud provider code locates at [upstream Kubernetes directory](https://github.com/kubernetes/kubernetes/tree/master/pkg/cloudprovider/providers/azure). If you want to create issues or pull requests for cloud provider, please go to [Kubernetes repository](https://github.com/kubernetes/kubernetes).

There is an ongoing work for refactoring cloud providers out of the upstream repository. For more details, please check [this issue](https://github.com/kubernetes/features/issues/88).

## Overview
`azure-cloud-controller-manager` is a Kubernetes component that provides interoperability with Azure API, and will be used by Kubernetes clusters running on Azure. It runs together with other components to provide the Kubernetes cluster’s control plane.

Using [cloud-controller-manager](https://kubernetes.io/docs/concepts/overview/components/#cloud-controller-manager) is a new alpha feature for Kubernetes since v1.6. `cloud-controller-manager` runs cloud provider related controller loops, which used to be run by `controller-manager`.

`azure-cloud-controller-manager` is a specialization of `cloud-controller-manager`. It depends on [cloud-controller-manager app](https://github.com/kubernetes/kubernetes/tree/master/cmd/cloud-controller-manager/app) and [azure cloud provider](https://github.com/kubernetes/kubernetes/tree/master/pkg/cloudprovider/providers/azure).

## Usage
You can use [acs-engine](https://github.com/Azure/acs-engine) to deploy a Kubernetes cluster running with cloud-controller-manager. It supports deploying `Kubernetes azure-cloud-controller-manager` for Kubernetes v1.8+.

## Development
Prerequisite:
- [golang](https://golang.org/doc/install)

Build project:
```
make
```

Build image:
```
make image
```

Run unit tests:
```
make test-unit
```

Updating dependency: (please check [Dependency management](docs/dependency-management.md) for additional information)
```
make update
```

Please also check following development docs:
- [Component versioning](docs/component-versioning.md)
- [Dependency management](docs/dependency-management.md)
- [E2E Tests](docs/e2e-tests.md)

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.microsoft.com.

When you submit a pull request, a CLA-bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., label, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
