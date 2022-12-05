# LABORATORY-KUBERNETES

## Commands

```bash
alias k=kubernetes
```

A list of interesting command to remember:

```bash
# Get all the context
$ k config get-context --no-headers

# Show the labels of every pods
$ k get pods --show-labels

# Get the pods and a particular colone
$ k get pods --no-headers | awk {'print $2'}

# Get the pods of every namespaces
$ k get pods -A

# Get everything in every namespaces
$ k get all -A

# Scale a deployment
$ k scale deploy <name> --replicas=X

# Create a pod in a yaml document
$ k run nginx --image nginx --labels=app=whatever,prod=2 --dry-run=client -o yaml > p.yaml

# Replace a resource by force
$ k replace --force -f /tmp/<name>

# Create a serviceaccount
$ k create sa <name> -n whatever

# Create a role
$ k -n whatever create role processor --resources=secrets,configmaps,pods --verbs=list,create

# create a rolebinding
$ k -n whatever create rolebinding processor --role processor --serviceaccount=whatever:processor

# Test a rolebinding
$ k -n ns2 auth can-i list secret --as system:serviceaccount:ns2:processor

# list resources
$ k api-resources

# List the containers
$ crictl ps

# logs a container
$ crictl logs

# Create a secret
$ k create secret generic secret2 --from-literal=user=user1

# Create a token for joining a node
$ kubeadm token create --print-join-command

# List the token
$ kubeadm token list
```

Useful commands:

```bash
# count lines
$ wc -l
```

## Links

- [Explanation maxSurge & maxUnavailable](https://www.bluematador.com/blog/kubernetes-deployments-rolling-update-configuration)
