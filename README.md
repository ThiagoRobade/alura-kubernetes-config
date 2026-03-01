# ☸️ Kubernetes: Pods, Services e ConfigMap

![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![YAML](https://img.shields.io/badge/yaml-%23ffffff.svg?style=for-the-badge&logo=yaml&logoColor=b12128)

## 📌 Sobre o Repositório

Este repositório documenta as configurações e manifestos YAML desenvolvidos durante o curso **[Kubernetes: Pods, Services e ConfigMap](https://cursos.alura.com.br/course/kubernetes-pods-services-configmap)**.

O objetivo principal deste projeto é consolidar o entendimento prático da orquestração de contêineres, focando na criação da infraestrutura declarativa necessária para rodar aplicações de forma escalável, garantindo a comunicação entre serviços e a injeção segura de variáveis de ambiente.

## 🏗️ Arquitetura e Recursos Explorados

Abaixo estão os detalhes técnicos de cada componente configurado neste repositório:

### 1. Pods (A Unidade Básica)
- **Definição Declarativa:** Criação de Pods utilizando arquivos `.yaml` em vez de comandos imperativos.
- **Ciclo de Vida e Troubleshooting:** Monitoramento do status dos Pods (Pending, Running, CrashLoopBackOff) e extração de logs para depuração de erros na inicialização dos contêineres.
- **Múltiplos Contêineres:** Entendimento do padrão de design de Pods que rodam mais de um contêiner compartilhando o mesmo *namespace* de rede e volumes.

### 2. Services (Comunicação e Exposição)
- **Labels e Selectors:** Mapeamento dinâmico entre Services e Pods utilizando rótulos, garantindo que o tráfego seja roteado corretamente mesmo quando os Pods são recriados.
- **ClusterIP:** Configuração do serviço padrão para comunicação interna e segura entre diferentes componentes dentro do próprio cluster.
- **NodePort:** Exposição de portas específicas em todos os nós (Nodes) do cluster para permitir o acesso externo à aplicação durante o ambiente de desenvolvimento/testes.

### 3. ConfigMaps (Desacoplamento de Configurações)
- **Criação Imperativa e Declarativa:** Geração de mapas de configuração tanto via linha de comando quanto via manifesto YAML.
- **Injeção de Variáveis de Ambiente:** Mapeamento de chaves do ConfigMap diretamente para o `env` dos contêineres, evitando hardcode de URLs de banco de dados ou credenciais no código da aplicação.
- **Montagem de Volumes:** Utilização de ConfigMaps como arquivos físicos montados dentro do sistema de arquivos do contêiner (`volumeMounts`).

## 💻 Cheat Sheet: Comandos Úteis

Uma lista dos comandos mais utilizados durante as práticas para gerenciar o cluster:

```bash
# Aplicar ou atualizar um manifesto
$ kubectl apply -f arquivo.yaml

# Listar recursos detalhadamente
$kubectl get pods -o wide$ kubectl get svc
$ kubectl get configmap

# Inspecionar um recurso específico para encontrar erros
$ kubectl describe pod <nome-do-pod>

# Visualizar logs da aplicação rodando no contêiner
$ kubectl logs <nome-do-pod>

# Deletar recursos criados
$ kubectl delete -f arquivo.yaml