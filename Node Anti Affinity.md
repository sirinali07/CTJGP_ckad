## Node Anti Affinity
```
vi na-nginx.yaml
```
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: na-nginx
spec:
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
        - matchExpressions:
          - key: disktype
            operator: NotIn   #In = NodeAffinity  #NotIn = NodeAntiAffinity
            values:
            - hdd    
  containers:
  - name: nginx
    image: nginx
    ```
 ```
kubectl apply -f vi na-nginx.yaml
 ```
 ```
kubectl get pod -o wide
 ```
