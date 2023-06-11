# Test Keda HPA

1. `curl -o hey https://storage.googleapis.com/hey-release/hey_darwin_amd64 && chmod a+x hey`

2. have a shell where do command `kubectl get pods -l=app=complains-app -w`,check as well `kubectl get hpa`

3. Do `hey -n 1000 -c 10 http://127.0.0.1:9090`
