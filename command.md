### Commande et explications

1. **Commandes générales**

<table>
	<tr> 
		<td>kubectl get pods</td>
		<td>Liste tous les pods dans le namespace actuel.</td>	
	</tr>
	<tr>
		<td>kubectl get pods -n `namespace` </td>
		<td>Liste les pods dans un namespace spécifique.</td>
	</tr>
	<tr>
		<td>kubectl get deployments</td>
		<td>Liste tous les déploiements (apps) dans le namespace actuel.</td>
	</tr>
	<tr>
		<td>kubectl get svc</td>
		<td>Liste tous les services (expositions réseau) dans le namespace actuel.</td>
	</tr>
	<tr>
		<td>kubectl get pvc</td>
		<td >Liste les PersistentVolumeClaims dans le namespace actuel.</td>
	</tr>
	<tr>
		<td>kubectl get pv</td>
		<td>Liste tous les PersistentVolumes (niveau cluster).</td>
	</tr>
    <tr>
        <td>kubectl get events</td>
        <td>Affiche les événements récents (triés par défaut par date).</td>
    </tr>
</table>


2. **Debug & observations**

<table>
	<tr> 
		<td>kubectl describe pod `pod-name` </td>
		<td>Affiche tous les détails sur un pod, y compris les événements à la fin.</td>	
	</tr>
	<tr>
		<td>kubectl describe deployment `deployment-name` </td>
		<td>Affiche les détails du déploiement (stratégies, pods liés, erreurs).</td>
	</tr>
	<tr>
		<td>kubectl logs `pod-name` </td>
		<td>Affiche les logs d’un pod (stdout/stderr).</td>
	</tr>
	<tr>
		<td>kubectl logs `pod-name` -c `container-name` </td>
		<td>Si ton pod a plusieurs conteneurs, tu peux cibler un conteneur.</td>
	</tr>
	<tr>
		<td>kubectl get pods -w</td>
		<td>Observe l’évolution des pods en temps réel (watch mode).</td>
	</tr>
</table>

3. **Actions & gestions**

<table>
	<tr> 
		<td>kubectl apply -f fichier.yaml </td>
		<td>Applique un fichier de configuration (création ou mise à jour d’objet).</td>	
	</tr>
	<tr>
		<td>kubectl delete -f fichier.yaml </td>
		<td>Supprime un objet à partir d’un fichier de config.</td>
	</tr>
	<tr>
		<td>kubectl delete pod `pod-name` </td>
		<td>Supprime un pod. Kubernetes le recrée automatiquement si c’est un déploiement.</td>
	</tr>
	<tr>
		<td>kubectl rollout restart deployment `deployment-name` </td>
		<td>Redémarre proprement un déploiement (utile après modif de config ou de volume).</td>
	</tr>
	<tr>
		<td>kubectl exec -it `pod-name` -- /bin/bash</td>
		<td>Ouvre un terminal dans le pod (si bash est installé).</td>
	</tr>
    <tr>
		<td>kubectl port-forward pod/`pod-name` 8080:80</td>
		<td>Redirige un port local vers un port du pod (utile pour tester en local).</td>
	</tr>
</table>

4. **Namespaces & configs**

<table>
	<tr> 
		<td>kubectl get ns </td>
		<td>Liste tous les namespaces.</td>	
	</tr>
	<tr>
		<td>kubectl config get-contexts </td>
		<td>Liste les contextes Kubernetes disponibles.</td>
	</tr>
	<tr>
		<td>kubectl config use-context <name> </td>
		<td> <name>	Change de contexte Kubernetes (utile si tu bosses sur plusieurs clusters).</td>
	</tr>
    <tr>
		<td>kubectl describe pvc rasa-pvc -n <namespace> </td>
		<td>Elle affiche tous les détails du PVC (PersistentVolumeClaim) nommé rasa-pvc dans le namespace .</td>
	</tr>
</table>


5. **Debugger un pod**

```bash
kubectl get pods -n <namespace> 
kubectl describe pod <nom-du-pod> -n <namespace> 
kubectl logs <nom-du-pod> -n <namespace> 
kubectl get pvc -n <namespace> 
kubectl describe pvc rasa-pvc -n <namespace>
```

6. **Créer un secret**

```bash
kubectl create secret docker-registry `name` \ 
  --docker-server=`your-registry-server` \
  --docker-username=`your-name` \
  --docker-password=`your-pword` \
  --docker-email=`your-email` -n `namespace`
```