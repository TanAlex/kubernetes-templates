kubectl -n kube-system create sa nginx-ingress-controller
kubectl apply -f https://gist.github.com/mgoodness/684d91e5812d383f6cc48d420bdad5b5/raw/8ef6d0623e9273aa93f22ab2b5d5cbb40502a5aa/nginx-ingress-controller-clusterrole.yaml
kubectl -n kube-system apply -f https://gist.github.com/mgoodness/4c5ddf4cc340a7c504a01a8f9ff422cf/raw/421d2032e4a36577739b60c0e673e889c1d1c6e2/nginx-ingress-controller-role.yaml
kubectl create clusterrolebinding nginx-ingress-controller --clusterrole nginx-ingress-controller --serviceaccount=kube-system:nginx-ingress-controller
kubectl -n kube-system create rolebinding nginx-ingress-controller --role nginx-ingress-controller --serviceaccount=kube-system:nginx-ingress-controller
kubectl -n kube-system patch rc/nginx-ingress-controller -p '{"spec": {"template": {"spec": {"serviceAccountName": "nginx-ingress-controller"}}}}'
kubectl -n kube-system delete po -l app=nginx-ingress-controller

