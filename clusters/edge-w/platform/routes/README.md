# Edge SNI routes

One file per workload cluster, named `<cluster>.yaml`, each holding that
cluster's `ServiceEntry` and SNI `VirtualService`. Files are written here by the
workload cluster's own vend, not by this cluster's bootstrap, so a cluster
registers and deregisters itself without any other lane changing.

There is deliberately no `kustomization.yaml` in this directory. Flux generates
one from whatever manifests it finds, which is what makes this an accumulator
rather than a central list that has to be kept in sync with the fleet.

This file is not a manifest and is ignored by Flux. It exists so the directory
is present in Git before the first workload cluster registers.
