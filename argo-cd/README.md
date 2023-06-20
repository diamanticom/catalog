# argo-cd
This folder contains the workload templates for argo-cd - a declarative, GitOps continuous delivery tool for Kubernetes.

# Create Catalog
1. Click ``Add Catalog`` button in Spektra and give a name for this catalog. We can call it argo-cd. The ``argo-cd`` will show up in the catalog list once successfully created.
2. Click on the ``argo-cd`` catalog to list the workload templates. Since no templates are created yet, it will be empty

The argo-cd application has two workload-templates, one for the CRD and the second for the rest of the Kubernetes objects for the application. These need to created as separate workload-templates.

## Add argo-cd CRD Workload Template
1. Click on ``Add Workload Template`` and select ``Create New``
2. In the configuration window, select the ``remote`` tab. Give the template a name, say ``crd``. Add the repository URL as ``https://raw.githubusercontent.com/diamanticom/catalog/main/argo-cd/crd.yaml``. Add a version for this template, say ``1.0``.
3. Click ``Add`` button to add the CRD to the workload template list.

## Add argo-cd Application Workload Template
1. Click on ``Add Workload Template`` and select ``Create New``
2. In the configuration window, select the ``remote`` tab. Give the template a name, say ``argocd``. Add the repository URL as ``https://raw.githubusercontent.com/diamanticom/catalog/main/argo-cd/argocd.yaml``. Add a version for this template, say ``1.0``.
3. Click ``Add`` button to add the CRD to the workload template list.

The workload templates are now created and ready to be installed on the target/tenant clusters managed by Spektra.

# Install Application

## Install CRD workload template
1. Click ``crd`` workload template and click ``Install``
2. Select the ``Project`` where the CRD needs to be installed. Since it is a CRD object, its scope is across all clusters included in the Project. Click ``Begin Install`` to create the CRDs on all clusters.
3. The ``Installations`` page will list the CRD objects created for each tenant cluster in the project. Once the CRDs are in ``Running`` state on the ``Installation`` page, the argo-cd application can be installed.

## Install argo-cd application
1. Click ``argocd`` workload template and click ``Install``
2. Select the ``Project`` and the cluster where argo-cd needs to be installed and click ``Begin Install``
3. It will take a few minutes for the installation to complete (to go into ``Running`` state).

## Accessing argo-cd URL (on Ultima Accelerator)
1. Click on the argocd Installation and look for the IP address of the ``argocd-server-*`` POD
2. On your browser, access the argo-cd URL at `http://<argocd-server-ip-address>:8080`

## Login information
1. The `Username` for login is `admin`
2. To get the password, you need kubectl access to the cluster. Run the following command to get the default password:
   `kubectl -n spektra-devtest-project-hybrid get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo`

> **Note**
> Replace the `spektra-devtest-project-hybrid` with the namespace associated with your project
