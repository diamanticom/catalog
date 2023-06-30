# ingress-controller
This folder contains the workload templates for ingress-controller - an nginx based load-balancer for Kubernetes

# Create Catalog
1. Click `Add Catalog` button in Spektra and give a name for this catalog. We can call it `ingress-controller`. The `ingress-controller` will show up in the catalog list once successfully created.
2. Click on the `ingress-controller` catalog to list the workload templates. Since no templates are created yet, it will be empty

## Add ingress-controller Application Workload Template
1. Click on `Add Workload Template` and select `Create New`
2. In the configuration window, select the `local` tab and select the `Helm Chart` option. Give the template a name, say `ingress-controller`.
3. Add a version for this template, say `1.0`. This version is different from the version of the Helm Chart being loaded.
4. Enter the Repo URL as `https://kubernetes.github.io/ingress-nginx`
5. Enter the Chart Name as `ingress-nginx`
6. Enter the version as `3.39.0`
7. Click `Add` button to add the helm-chart to the workload template list.

The workload template is now created and ready to be installed on the target/tenant clusters managed by Spektra.

# Install Application

## Install ingress-controller
1. Click `ingress-controller` workload template and click `Install`
2. Select the `Project` and the cluster where ingress-controller needs to be installed and click `Begin Install`. In this example, the project `ingress` was created and the tenant cluster was added to this project.
3. It will take a couple of minutes for the installation to complete (to go into `Running` state).
