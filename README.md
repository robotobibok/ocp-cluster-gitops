# ocp-cluster-gitops



bootstrap - instalacja gitops/argo na klastrze + dodanie uprawnien
```    oc apply -k ocp02-eskom-demo/bootstrap/overlays/default/
        clusterrolebinding.rbac.authorization.k8s.io/cluster-admin-for-ocpgitops created
        Warning: resource argocds/openshift-gitops is missing the kubectl.kubernetes.io/last-applied-configuration annotation which is required by oc apply. oc apply should only be used on resources created declaratively by either oc create --save-config or oc apply. The missing annotation will be patched automatically.
        argocd.argoproj.io/openshift-gitops configured
        subscription.operators.coreos.com/openshift-gitops-operator created```

components - rzeczy dla kontrolera gitops, zeby mogl dzialac, np applicationsets etc
```     oc apply -k ocp02-eskom-demo/bootstrap/overlays/default/
        clusterrolebinding.rbac.authorization.k8s.io/cluster-admin-for-ocpgitops unchanged
        appproject.argoproj.io/test-project created
        argocd.argoproj.io/openshift-gitops configured
        subscription.operators.coreos.com/openshift-gitops-operator unchanged```

core - wszystkie podstawowe komponenty/konfigi itd dla klastra, applicationsety wskazuja tutaj
```     oc apply -k ocp02-eskom-demo/core/gitops-controller
        clusterrolebinding.rbac.authorization.k8s.io/cluster-admin-for-ocpgitops unchanged
        appproject.argoproj.io/test-project unchanged
        argocd.argoproj.io/openshift-gitops configured
        subscription.operators.coreos.com/openshift-gitops-operator unchanged```

po dodaniu appsetu juz argo czuwa nad tym repo i je automatycznie wczytuje
```oc apply -k ocp02-eskom-demo/core/gitops-controller
clusterrolebinding.rbac.authorization.k8s.io/cluster-admin-for-ocpgitops unchanged
appproject.argoproj.io/test-project unchanged
applicationset.argoproj.io/cluster created
argocd.argoproj.io/openshift-gitops configured
subscription.operators.coreos.com/openshift-gitops-operator unchanged```



tenants - aplikacje 


until oc apply -k ocp02-eskom-demo/bootstrap/overlays/default; do sleep 3; done


oc get apps / appsets -n openshift-gitops


teraz mozna dodawac kolejne rzeczy w components (admin) lub tenants (aplikacje biznesowe)