
$ kubectl run -i oneshot \
 --image=gcr.io/kuar-demo/kuard-amd64:blue \
 --restart=OnFailure \
 -- --keygen-enable \
 --keygen-exit-on-complete \
 --keygen-num-to-gen 10



# equivalent yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: oneshot
spec:
  template:
    spec:
      containers:
      - name: kuard
        image: gcr.io/kuar-demo/kuard-amd64:blue
        imagePullPolicy: Always
        args:
        - "--keygen-enable"
        - "--keygen-exit-on-complete"
        - "--keygen-num-to-gen=10"
      restartPolicy: OnFailure

# Run 5 pods in parallel and total do 10 pods jobs
apiVersion: batch/v1
kind: Job
metadata:
  name: oneshot
spec:
  parallelism: 5
  completions: 10
  template:
    metadata:
      labels:
        chapter: jobs
    spec:
      containers:
      - name: kuard
        image: gcr.io/kuar-demo/kuard-amd64:blue
        imagePullPolicy: Always
        args:
        - "--keygen-enable"
        - "--keygen-exit-on-complete"
        - "--keygen-num-to-gen=10"
      restartPolicy: OnFailure