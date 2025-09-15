# Debug Operations for Pods in Kubernetes  
The kubectl command line interface, provided by Kubernetes, contains several commands that you can use to figure out what is happening in your cluster. The commands described in this topic can help you assess why your pod isn't performing as expected.

Before you begin working with kubectl, perform the following tasks:  
- Make sure you have installed kubectl.
- Make sure you have access to the cluster you want to debug.
- Connect kubectl to your cluster. 

## View the Pods in your Cluster  
First find the pod you want to debug. Use a `kubectl get` command to see a list of the pods in your cluster.  

```shell
kubectl get pods 
``` 

You can focus this list to a specific namespace using the `--namespace` flag, for example:  

```shell
kubectl get pods --namespace <my-namespace>
``` 

Find the name of the pod that you want to debug in the output from this command. 

## Get the Logs for your Pod  
Use the `kubectl logs` command to show the logs for a pod.

```shell
kubectl logs <my-pod> 
``` 

You can focus this command on a specific container in the pod using the `-c` flag, for example:  

```shell
kubectl logs <my-pod> -c <my-container> 
``` 

You can use the output from this command to see what has been happening in your pod.  

##  Issue a Command against a Container in a Pod  
Use the `kubectl exec` command to issue a command against a container in a pod.  

```shell
kubectl exec <my-pod> -c <my-container> -- <my-command> 
```  

For more information on the syntax and usage of this command, see the description of [kubectl exec](https://kubernetes.io/docs/reference/kubectl/generated/kubectl_exec/) in the Kubernetes Documentation.  

## Clone a Pod to Debug  
Using a clone of a pod (rather than the pod itself) allows you to use some common debugging operations and assess errors without worrying about the pod terminating. Use the `kubectl debug` command to create a clone of a pod that does not terminate when an error occurs.  

```shell
kubectl debug <my-pod>
``` 

For more information on the syntax and usage of this command, see the description of [kubectl debug](https://kubernetes.io/docs/reference/kubectl/generated/kubectl_debug/) in the Kubernetes Documentation.  

## For More Information  

For more helpful information about these and other kubectl commands that are useful for debugging, see the following articles in the [Kubernetes Documentation at kubernetes.io](https://kubernetes.io/docs/home/):  

- [Debug Pods](https://kubernetes.io/docs/tasks/debug/debug-application/debug-pods/)
- [Monitoring, Logging, and Debugging](https://kubernetes.io/docs/tasks/debug/)
- [Command line tool (kubectl)](https://kubernetes.io/docs/reference/kubectl/)
- [Getting Started (with kubectl)](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#-strong-getting-started-strong-) 
- [What is Kubernetes](https://kubernetes.io/docs/concepts/overview/) 
