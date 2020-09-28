kubectl -n kube-system create sa kubernetes-dashboard
kubectl create clusterrolebinding kubernetes-dashboard --clusterrole cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
kubectl -n kube-system patch rc/kubernetes-dashboard -p '{"spec": {"template": {"spec": {"serviceAccountName": "kubernetes-dashboard"}}}}'
kubectl -n kube-system delete po -l app=kubernetes-dashboard