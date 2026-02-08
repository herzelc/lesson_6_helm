# My App Helm Chart
 ## Purpose of Each Resource 
    Deployment: Manages the application pods, ensuring the requested number of replicas are running. 
    DaemonSet:  Ensures that a copy of the pod runs on every node in the cluster. 
    Service:  Exposes the application to internal/external traffic.
    Job: Performs one-time initialization tasks using Helm Hooks. 
    ConfigMap: Stores non-sensitive configuration (e.g., app messages). 
    Secret: Stores sensitive data (e.g., API tokens).
 
 ## Commands Used 
    1. Install: `helm upgrade --install myapp ./charts/myapp`
    2. History: `helm history myapp` 
    3. Rollback: `helm rollback myapp 1` 
    4. Uninstall: `helm uninstall myapp` 

 ## Verification Steps 
    1. Check pods status: `kubectl get pods` 
    2. Verify logs for injected data: `kubectl logs -l app=myapp-deploy` 
    3. Check ConfigMap/Secret: `kubectl get configmap,secret`

 ## Helm Lifecycle Explanation
     The Helm lifecycle manages the creation, updating, and deletion of Kubernetes resources as a single unit (Release). It tracks versions through "Revisions," allowing for easy rollbacks and state management.
 
 ## Why `helm upgrade --install` is preferred?
     It is "Idempotent" – it checks if the release exists. If it doesn't, it installs it; if it does, it updates it. This is ideal for CI/CD pipelines as it prevents errors regardless of the current state.
 
 ## Template & Resource Explanation 
    Deployment/DaemonSet: Use `env.valueFrom` to inject ConfigMaps and Secrets.
    Job: Uses `post-install` hooks to run setup tasks only after the main resources are ready.
    Secrets: Base64 encoded for security, unlike plain-text ConfigMaps
