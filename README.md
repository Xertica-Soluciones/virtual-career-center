![image](https://github.com/user-attachments/assets/a1a596ee-eade-4774-837e-bd46552af9c4)
# Kubernetes (K8s) 

[![CII Best Practices](https://bestpractices.coreinfrastructure.org/projects/569/badge)](https://bestpractices.coreinfrastructure.org/projects/569) [![Go Report Card](https://goreportcard.com/badge/github.com/kubernetes/kubernetes)](https://goreportcard.com/report/github.com/kubernetes/kubernetes)

<img src="https://github.com/kubernetes/kubernetes/raw/master/logo/logo.png" width="100">

----
# Visão Geral

É uma plataforma baseada em nuvem que utiliza algoritmos de IA Generativa, Machine Learning e Processamento de Linguagem Natural para melhorar a empregabilidade do aluno por meio de:
▷    Geração automática de currículo
▷    Matching de vaga-candidato e candidato-vaga
▷    Geração de insights estratégicos sobre o mercado de trabalho local

# Descrição de Suporte

Agradecemos por entrar em contato com o suporte do Xertica Virtual Career Center no Google Cloud Marketplace. Estamos aqui para ajudá-lo(a) com qualquer dúvida ou problema que você possa ter.

Para que possamos atender à sua solicitação da melhor forma possível, pedimos que inclua as seguintes informações em seu e-mail: vcc-suporte@xertica.com

ID do projeto do Google Cloud: O ID do projeto onde você está utilizando o [Nome do seu produto].
Descrição do problema: Detalhe o problema que você está enfrentando, incluindo os passos que você tomou e os resultados obtidos. Se possível, inclua capturas de tela ou logs de erro.
Informações de contato: Seu nome, endereço de e-mail e número de telefone para que possamos entrar em contato, caso necessário.
Nosso objetivo é responder à sua solicitação o mais rápido possível. O tempo de resposta pode variar dependendo da complexidade do problema e do volume de solicitações.

# Url de suporte
```bash
https://www.xertica.ai/en/contact
```
# Deploy da Aplicação no Kubernetes

Este repositório contém os arquivos necessários para fazer o deploy da aplicação no Kubernetes. Siga os passos abaixo para aplicar todos os arquivos de deployment.

Para obter os arquivos de instalação, entre em contato com o suporte.

## Estrutura de Arquivos

- `k8s/deployment.yaml`: Deployment do frontend.
- `k8s/service.yaml`: Service para expor o frontend.
## Criação do Cluster

```bash
gcloud container clusters create-auto [NOME_DO_CLUSTER] \
    --region [REGIÃO] \
    --project [ID_DO_PROJETO]
```
## Conectar ao Cluster

Se ainda não estiver autenticado, faça login na sua conta do Google Cloud:

```bash
gcloud auth login
```

Certifique-se de que você está utilizando o projeto Google Cloud correto:

```bash
gcloud config set project [ID_DO_PROJETO]
```

Use o comando abaixo para obter as credenciais do cluster e configurá-las no `kubectl`:

```bash
gcloud container clusters get-credentials [NOME_DO_CLUSTER] \
    --region [REGIÃO] \
    --project [ID_DO_PROJETO]
```

Para verificar se a conexão foi estabelecida corretamente, execute:

```bash
kubectl get nodes
```
## Como Aplicar os Arquivos de Deployment

Para aplicar todos os arquivos de deployment, execute os comandos abaixo:

```bash
kubectl create namespace vcc
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```
----

# Processo de desinstalação do kubernetes

![image](https://github.com/user-attachments/assets/7b08a6f3-ca09-41a3-8522-6c0e4b6acd5a)

Para desinstalar ou remover os recursos criados no Kubernetes via CLI, você precisa excluir os deployments, serviços e outros recursos que foram aplicados durante a instalação.

Abaixo, é apresentado o passo a passo para a desinstação da aplicação:

## Conectar ao Cluster

Primeiro, certifique-se de que você está conectado ao cluster Kubernetes onde os recursos foram implantados. Se você já está conectado (como descrito no processo de instalação), pode pular essa etapa.

Caso contrário, siga as etapas de autenticação e conexão ao cluster:

```bash
gcloud auth login
gcloud config set project [ID_DO_PROJETO]
gcloud container clusters get-credentials [NOME_DO_CLUSTER] \
    --region [REGIÃO] \
    --project [ID_DO_PROJETO]
```

## Excluir os Recursos de Deployment e Serviço

Execute os comandos abaixo para excluir os deployments e serviços que você aplicou anteriormente:

```bash
kubectl delete -f k8s/deployment.yaml -n [NOME_DO_NAME_SPACE]
kubectl delete -f k8s/service.yaml -n [NOME_DO_NAME_SPACE]
```

Esses comandos excluem os deployments e serviços especificados nos arquivos YAML.

## Excluir o Namespace (Opcional)

Se o namespace foi criado exclusivamente para essa aplicação e você deseja removê-lo, pode excluir o namespace inteiro. Isso irá remover todos os recursos dentro dele:

```bash
kubectl delete namespace [NOME_DO_NAME_SPACE]
```

**Atenção**: Excluir um namespace irá remover todos os recursos (deployments, serviços, pods, etc.) que estão dentro dele. Use este comando com cuidado.

## Verificar a Exclusão

Após a exclusão dos recursos, você pode verificar se tudo foi removido corretamente:

```bash
kubectl get all -n [NOME_DO_NAME_SPACE]
```
