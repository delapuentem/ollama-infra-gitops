# ollama-infra-gitops

Para asegurar el target de donde va a ir Ollama, generalmente a una máquina worker con más recursos para ejecutar modelos LLM, utilizamos un label para el worker de Kubernetes.

```bash
sudo k0s kubectl label node kubernetes-node2 type=ollama-ia
```

Listamos las labels para asegurarnos que se ha aplicado correctamente

```bash
sudo k0s kubectl get nodes --show-labels
```

Descargamos un modelo que irá al storageClass del Deployment, y creará un Pod en el worker con el label ollama-ia en el namespace de ollama

```bash
sudo k0s kubectl exec -it -n ollama $(sudo k0s kubectl get pod -n ollama -l app=ollama -o name) -- ollama pull llama3.2
```

Listar modelos LLM descargados y guardados en disco

```bash
sudo k0s kubectl exec -it -n ollama $(sudo k0s kubectl get pod -n ollama -l app=ollama -o name) -- ollama list
```
