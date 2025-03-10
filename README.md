# vSphere CSI chart

This repository contains the chart which is used for deploying the vSphere CSI (Container Storage Interface) driver on Giant Swarm CAPV clusters.

## Updating the chart

Updates are handled via the `Makefile.custom.mk` Makefile which has three targets.

### `make update-csi-chart`

Updates to the chart are handled by Renovate via the [Chart.yaml](./config/vsphere-csi-driver/overwrites/Chart.yaml) in the overwrites `directory`. When this target is run,
the chart is updated from the [upstream repository](https://github.com/kubernetes-sigs/vsphere-csi-driver) to the version specified in `Chart.yaml` in the `overwrites` directory.

### `make apply-custom-patches-for-csi`

This target applies custom patches to the chart which cannot be handled by Kustomize.

### `make increase-chart-version`

This target should be run last as it increases the version of the chart in the `Chart.yaml` file in the `helm` directory (the earlier targets may overwrite this file).
