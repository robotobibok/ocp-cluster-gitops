# ocp-cluster-gitops



bootstrap - instalacja gitops/argo na klastrze + dodanie uprawnien
    oc apply -k ocp02-eskom-demo/bootstrap/overlays/default/
        clusterrolebinding.rbac.authorization.k8s.io/cluster-admin-for-ocpgitops created
        Warning: resource argocds/openshift-gitops is missing the kubectl.kubernetes.io/last-applied-configuration annotation which is required by oc apply. oc apply should only be used on resources created declaratively by either oc create --save-config or oc apply. The missing annotation will be patched automatically.
        argocd.argoproj.io/openshift-gitops configured
        subscription.operators.coreos.com/openshift-gitops-operator created

components - rzeczy dla kontrolera gitops, zeby mogl dzialac, np applicationsets etc
