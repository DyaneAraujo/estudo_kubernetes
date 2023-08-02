# estudo_kubernetes

https://kubernetes.io/pt-br/docs/tutorials/kubernetes-basics/explore/explore-intro/

## Para que serve o Kubernetes

<p>O kubernetes resolve o problema de escalabilidade horizontal, dividindo o poder computacional das máquinas e trabalhando em paralelo. O Kubernetes 
é capaz de fazer isso, ele gerencia uma ou múltiplas máquinas trabalhando em conjunto, que nós vamos chamar de cluster. O Kubernetes é capaz de criar 
esse cluster e o gerenciar para nós.</p>
<p>O Kubernetes é capaz de criar e gerenciar um cluster para que nós consigamos manter a nossa aplicação escalável sempre que nós quisermos adicionar 
novos containers, sempre que nós quisermos reiniciar a nossa aplicação de maneira automática, caso ela tenha falhado. Então nós chamamos isso de 
orquestração de containers.</p>

<img width="989" alt="Screen Shot 2023-07-24 at 7 00 23 PM" src="https://github.com/DyaneAraujo/estudo_kubernetes/assets/114944655/6a917580-92aa-4268-b9d7-9a3a44e8a6df">

## Como o Kubernetes funciona

<p>O Kubernetes vai gerenciar um cluster, e as máquinas dentro de um cluster recebem denominações diferentes.</p>

<p>Elas podem ser master, onde o master é responsável por coordenar e gerenciar todo o nosso cluster e nós temos os notes que são responsáveis pela 
<p>execução do trabalho duro, para executar os nossos pods em capsulas containers, por assim dizer</p>
    
<img width="939" alt="Screen Shot 2023-07-24 at 7 31 35 PM" src="https://github.com/DyaneAraujo/estudo_kubernetes/assets/114944655/24ba9bd1-613b-4ca1-8d83-15feb05138a4">

<img width="843" alt="Screen Shot 2023-07-24 at 7 34 45 PM" src="https://github.com/DyaneAraujo/estudo_kubernetes/assets/114944655/8ac69a4c-2cb1-477c-9135-678195f9c9f7">

## Quais são os principais componentes da ferramenta

<p>Os resources do kubernetes já têm soluções ali implementadas para determinadas tipos de caso. Então nós temos, por exemplo: pods, ReplicaSets, 
Deployments, Volumes.</p>

<p>Então, por exemplo: se eu quero lidar com a questão de persistência de dados eu posso utilizar um recurso já pronto, que é o Persistent Volume. Então,
se eu quero e devo utilizar e encapsular um container para utilizar no Kubernetes, eu utilizo um pod.</p>

<p>Utilizando esses recursos nós conseguimos construir aplicações bem elaboradas; onde, por exemplo, nós recebemos um tráfego de dados no nosso session,
no nosso serviço e ele consegue fazer o balanceamento de cargas entre os pods que nós temos dentro da nossa aplicação.</p>

<p>Esses pods podem estar sendo gerenciados por um ReplicaSet que pode estar sendo gerenciado por um deployment e pode ser escalado. Nós podemos aumentar
o número de pods, um horizontal pod autoscaler.</p>
 
<img width="987" alt="Screen Shot 2023-07-24 at 7 05 49 PM" src="https://github.com/DyaneAraujo/estudo_kubernetes/assets/114944655/6a812e0c-e8ba-48c7-aeb6-cee85915524d">
  
## O que é, e para o que serve a API

<p>A API, além de receber as ordens do mundo externo e do que nós queremos fazer com o nosso cluster, ela é responsável por manter a comunicação com 
Controller Manager, um ETCD, com Scheduler e também os nossos nodes. Então através dela, nós conseguimos criar um pod, editar um ReplicaSet, ler os 
dados no Deployment, deletar um Volume - tudo isso através da API, nós nunca vamos nos comunicar diretamente com os outros componentes; vai ser sempre 
através da API.</p>

![image](https://github.com/DyaneAraujo/estudo_kubernetes/assets/114944655/1dc36309-0fe9-45f4-b366-9ac396556808)

## O que é, e para o que serve o kubectl

<p>O Kubectl, que nos provê as funcionalidades de criar, ler, atualizar e remover os dados do nosso cluster, os componentes do nosso cluster, os 
nossos recursos.</p>

<p>Então, através do Kubectl nós conseguimos fazer isso de maneira declarativa ou imperativa. Nós podemos criar arquivos de definição, ou executarmos 
comandos, que simplesmente vão fazer essa mágica acontecer.</p>

<p>E tudo isso ainda vai ser enviado um request do nosso Kubectl para a nossa API REST, que vai fazer a mágica acontecer dentro do nosso cluster.</p>

## O que é Nodes

<p>Um nó é a menor unidade de hardware de computação no Kubernetes. É uma representação de uma única máquina no seu cluster.
Na maioria dos sistemas de produção, um nó provavelmente será uma máquina física em um datacenter ou uma máquina virtual hospedada em um provedor 
de nuvem, como o Google Cloud Platform.</p>

## Criando e entendendo pods

### Entendendo o que são pods

<p>No Docker nós trabalhamos com container. E a partir de agora no Kubernetes nós vamos criar, produzir, manipular e gerir, não mais os containers 
diretamente, e sim os nossos pods. Então o mundo kubernetes, pods, o mundo Docker e containers.</p>

![Screen Shot 2023-08-02 at 6.15.41 PM.png](..%2FDesktop%2FScreen%20Shot%202023-08-02%20at%206.15.41%20PM.png)

<p>Um pod é um conjunto de um ou mais containers, então quando nós tivermos aqui a comunicação da nossa máquina com o kubectl para API, nós não vamos 
pedir pela criação diretamente de um container, e sim de um pod, que pode conter um ou mais containers dentro dele.</p>
<p>Isso sempre de maneira declarativa ou imperativa.</p>

![Screen Shot 2023-07-25 at 6.18.57 PM.png](..%2FDesktop%2FScreen%20Shot%202023-07-25%20at%206.18.57%20PM.png)
![Screen Shot 2023-07-25 at 6.19.18 PM.png](..%2FDesktop%2FScreen%20Shot%202023-07-25%20at%206.19.18%20PM.png)

<p>Dentro de um pod nós temos liberdade, para termos mais containers, mas sempre que nós criamos um pod ele ganha um endereço IP.</p>

<p>Então o endereço IP não é mais do container, e sim do nosso pod. Dentro do nosso pod nós temos total liberdade de fazermos um mapeamento de 
portas para os IPs que são atribuídos a esse pod.</p>

<p>No momento em que nós fazemos a requisição aqui, por exemplo, para o IP 10.0.0.1, repare que é o mesmo IP que nós estamos a fazer requisição 
para o IP do pod na porta 8080. Nós estamos nos referindo nesse momento ao nosso container dentro da porta :8080 no nosso pod.</p>

![Screen Shot 2023-07-25 at 6.20.29 PM.png](..%2FDesktop%2FScreen%20Shot%202023-07-25%20at%206.20.29%20PM.png)

<p>Nós vimos que nós temos um container ou mais dentro de um pod. Caso esse container falhe, o que vai acontecer?</p>

<p>Nesse momento, esse pod vai parar de funcionar. Ele morreu para sempre e o kubernetes tem total liberdade de criar um pod para substituir 
o antigo, mas não necessariamente com o mesmo IP que ele tinha antes, nós não temos controle sobre isso.</p>

![Screen Shot 2023-07-25 at 6.22.36 PM.png](..%2FDesktop%2FScreen%20Shot%202023-07-25%20at%206.22.36%20PM.png)
![Screen Shot 2023-08-02 at 6.30.17 PM.png](..%2FDesktop%2FScreen%20Shot%202023-08-02%20at%206.30.17%20PM.png)

<p>Por quê? Porquê os pods são efémeros, eles estão ali para serem substituídos a qualquer momento e toda criação de um novo pod é um novo pod 
efetivamente, não é o mesmo pod antigo renascido.</p>

<p>E caso nós tivéssemos mais de um container no mesmo pod, o que iria acontecer se esse pod falhasse? Para ele falhar efetivamente nós 
teríamos que ter a seguinte condição:</p>

<p>O primeiro container falhou dentro de um pod. Caso ainda tenha algum container em funcionamento sem nenhum problema dentro desse mesmo pod, 
ele ainda está saudável; mas caso nenhum container mais esteja a funcionar dentro desse pod, esse pod foi finalizado e outro vai ser criado no lugar dele.</p>

![Screen Shot 2023-07-25 at 6.22.52 PM.png](..%2FDesktop%2FScreen%20Shot%202023-07-25%20at%206.22.52%20PM.png)

<p>O IP pertence ao pod, e não aos containers. Isso quer dizer que no fim das contas, eles vão compartilhar os mesmos namespaces de rede e de processo, 
de comunicação entre o processo e eles também podem compartilhar volume.</p>

![Screen Shot 2023-07-25 at 6.24.22 PM.png](..%2FDesktop%2FScreen%20Shot%202023-07-25%20at%206.24.22%20PM.png)

<p>Qual é a grande vantagem deles compartilharem o mesmo IP? A grande vantagem é que agora eles podem fazer essa comunicação diretamente entre eles 
via localhost, porque eles têm o mesmo IP, sendo 10.0.0.1, nesse caso.</p>

<p>Então, agora nós temos essa capacidade de fazer uma comunicação de maneira muito mais fácil entre containers de um mesmo pod e isso, é claro, 
nós também vamos ter total capacidade de comunicar pods entre diferentes IPs. Eu tenho um pod com IP 10.0.0.1, ele pode começar com pod de IP 10.0.0.2. 
Por exemplo:</p>

![Screen Shot 2023-07-25 at 6.24.45 PM.png](..%2FDesktop%2FScreen%20Shot%202023-07-25%20at%206.24.45%20PM.png)

### Criando cluster

<p>Ambiente virtualizado com cluster com driver do docker ou virtualbox</p>

```shell
sudo install minikube

minikube start --vm-driver=docker

minikube start --vm-driver=virtualbox
```

* Comando para consultar os nodes

```shell
~ % kubectl get nodes                
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   8d    v1.27.3
```

### Criando pod

* Comando para criar um pod com a image nginx versão latest

```shell
kubectl run nginx-pod --image=nginx:latest
```

* Comando para consultar os pods

```shell
kubectl get pods
```

* Para acompanhar a criação do pod em tempo real

```shell
kubectl get pods --watch
```

* Comando para exibir detalhes sobre o pod, como inicialização, IP, porta, container, versão, labels e etc.

```shell
kubectl describe pod nginx-pod
```

<p>O pod é somente criado após a inicialização do container.</p>

* Comando para editar um pod

kubectl edit pod nginx-pod

Após dar enter no comando, apertar a tecla **i** para entrar no modo **INSERT**, após editar o arquivo aperta a tecla **ESC**
e escrever **:wq** para salvar e sair do modo vim.