# Component Versioning

## Components
### 1. Main package
- Main dockerfile: [Dockerfile](/Dockerfile)
    
    Update golang version in `FROM golang:*`

    Update `FROM buildpack-deps:*` if base image version changes.

- Travis CI config: [.travis.yml](/.travis.yml)
  
  Update golang version in following place:
    ```
    go:
    - *
    ```

- Test deployment image: [linux.json](/test/k8s-azure/manifest/linux.json)

  Update `customCcmImage` to latest stable released image, this is used for local deployment.

### 2. Kubernetes in E2E test
Following Kubernetes versions should stick to Kubernetes package version specified in [glide.yaml](/glide.yaml), please see [Dependency management](dependency-management.md) for details about package versions.

   - Test cluster hyperkube Image: [linux.json](/test/k8s-azure/manifest/linux.json)
     
     Update `"customHyperkubeImage": "*"` for Kubernetes version.

   - E2E tests: [Dockerfile](/test/k8s-azure/Dockerfile)
 
     Update `ARG K8S_VERSION=` for Kuberentes version.
 
     Update `FROM golang:* AS build_kubernetes`. This should stick to the Go version used by [Kubernetes](https://github.com/kubernetes/kubernetes/blob/master/build/build-image/cross/Dockerfile)

### 3. acs-engine in E2E test
   Edit file [Dockerfile](/test/k8s-azure/Dockerfile)

   Update `ARG ACSENGINE_VERSION=` for acs-engine version.

   Update `FROM golang:* AS build_acs-engine`.
   This should stick to the Go version used by [acs-engine](https://github.com/Azure/acs-engine/blob/master/Dockerfile).

## Kubernetes version update

To summary changes need when updating Kubernetes version: please update corresponding lines in following files.
- [glide.yaml](/glide.yaml)
- [linux.json](/test/k8s-azure/manifest/linux.json)
- [Dockerfile](/test/k8s-azure/Dockerfile)
