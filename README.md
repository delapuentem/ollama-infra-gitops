# ollama-infra-gitops

Para asegurar el target de donde va a ir Ollama, generalmente a una máquina worker con más recursos para ejecutar modelos LLM, utilizamos un label para el worker de Kubernetes.

```bash
sudo k0s kubectl label node kubernetes-node2 type=ollama-ia
```

Listamos las labels para asegurarnos que se ha aplicado correctamente

```bash
sudo k0s kubectl get nodes --show-labels
```
