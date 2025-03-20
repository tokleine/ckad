## Resource description
- Get details of a resource: ``kubectl describe po nginx``
- Get logs of a resource: `kubectl logs -f <name>`
- Watch a container: `kubectl get po nginx -w`
- Get infos of e.g. pod: 
	- `kubectl get pod nginx -o jsonpath='{.metadata.managedFields[0].apiVersion}'`
	- `kubectl get pod nginx -o jsonpath='{.status.podIP}'` -> works without having to traverse the entire json
	- `k8s get po -o jsonpath='{.items[*].status.podIP}'` -> gets IP of all pods

## Resource creation
- Create yaml for a resource: `kubectl run <name> --dry-run=client -o yaml --image=nginx > my.yaml`
- Create a Resource Quota: `kubectl create quota myrq --hard=cpu=1,memory=1G,pods=2 --dry-run=client -o yaml`

## Resource change/edit
- Update resource: `kubectl set image po/nginx nginx=nginx:1.24.0`

## Temporary stuff
- Run a command in a container: `kubectl run busybox --image=busybox --restart=Never -it --rm -n mynamespace --command -- env`
- Start shell in container: `k8s exec nginx -it -- /bin/sh`
- Run command in container: `k8s run busy --image=busybox --restart=Never -it --command -- /bin/sh -c "echo 'Hello world'"`