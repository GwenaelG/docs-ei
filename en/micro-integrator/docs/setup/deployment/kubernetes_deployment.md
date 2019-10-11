# Kubernetes Deployment

## k8s-ei-operator
Provides native support for the Kubernetes Ecosystem with WSO2 Micro Integrator.
The k8s-ei-operator allows you to deploy your integration solutions as an **Integration** kind into the Kubernetes environment built on top of [WSO2 Integration Studio](../../../develop/WSO2-Integration-Studio). 

## Prerequisites
The k8s-ei-operator is built with operator-sdk v0.7.0 and supported in the following environment.

>   [Kubernetes](https://kubernetes.io/docs/setup/) cluster and client v1.11+

## Install k8s-ei-operator
Please do the following steps (one time) to configure the Kubernetes environment in your server/machine.

2.  Clone the **k8s-ei-operator** GitHub repository.
    ```bash
    git clone https://github.com/wso2/k8s-ei-operator.git
    ```
2.  Change directory to k8s-ei-operator.
    ```bash
    cd k8s-ei-operator
    ```
3.  Setup Service Account.
    ```bash
    kubectl create -f deploy/service_account.yaml
    ```
5.  Setup RBAC.
    ```bash
    kubectl create -f deploy/role.yaml
    kubectl create -f deploy/role_binding.yaml
    ```
6.  Deploy CustomResourceDefinition into the Kubernetes cluster to understand custom resource type.
    ```bash
    kubectl create -f deploy/crds/integration_v1alpha1_integration_crd.yaml
    ```
7.  Deploy the k8s-ei-operator.
    ```bash
    kubectl create -f deploy/operator.yaml
    ```
    
## Deploy Kubernetes Cluster

-   Run the following command to deploy the **kubernetes_cr.yaml** configuration file (stored in the <MAVEN_MULTI_MODULE_PROJECT>/<KUBERNETES_PROJECT> directory), which is generated by the [Kubernetes Exporter Project](https://ei.docs.wso2.com/en/latest/micro-integrator/develop/create-kubernetes-project/).
    ```bash
    kubectl apply -f path/to/kubernetes_cr.yaml
    ```
    
## Run the Solution

-   Port forward to expose the cluster port:
    ```bash
    kubectl port-forward service/<deployment-name>-service 8290:8290
    ```
-   Invoke the service/API using curl.   