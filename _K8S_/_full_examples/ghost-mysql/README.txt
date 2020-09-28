$ kubectl create cm --from-file ghost-config.js ghost-config

$ kubectl apply -f ghost.yaml

$ kubectl expose deployments ghost --port=2368

$ kubectl proxy

# Visit http://localhost:8001/api/v1/namespaces/default/services/ghost/proxy/ 

