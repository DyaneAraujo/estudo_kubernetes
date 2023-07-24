# estudo_kubernetes

- ## Para que serve o Kubernetes
  * O kubernetes resolve o problema de escalabilidade horizontal, dividindo o poder computacional das máquinas e trabalhando em paralelo. O Kubernetes é capaz de fazer isso, ele gerencia uma ou múltiplas máquinas trabalhando em conjunto, que nós vamos chamar de cluster. O Kubernetes é capaz de criar esse cluster e o gerenciar para nós.
  * O Kubernetes é capaz de criar e gerenciar um cluster para que nós consigamos manter a nossa aplicação escalável sempre que nós quisermos adicionar novos containers, sempre que nós quisermos reiniciar a nossa aplicação de maneira automática, caso ela tenha falhado. Então nós chamamos isso de orquestração de containers.

   <img width="989" alt="Screen Shot 2023-07-24 at 7 00 23 PM" src="https://github.com/DyaneAraujo/estudo_kubernetes/assets/114944655/6a917580-92aa-4268-b9d7-9a3a44e8a6df">

- ## Como o Kubernetes funciona
  * O Kubernetes, como eu falei para vocês, vai gerenciar um cluster, e as máquinas dentro de um cluster recebem denominações diferentes.

  * Elas podem ser master, onde o master é responsável por coordenar e gerenciar todo o nosso cluster e nós temos os notes que são responsáveis pela execução do trabalho duro, para executar os nossos pods em capsulas containers, por assim dizer
    
<img width="939" alt="Screen Shot 2023-07-24 at 7 31 35 PM" src="https://github.com/DyaneAraujo/estudo_kubernetes/assets/114944655/24ba9bd1-613b-4ca1-8d83-15feb05138a4">

<img width="843" alt="Screen Shot 2023-07-24 at 7 34 45 PM" src="https://github.com/DyaneAraujo/estudo_kubernetes/assets/114944655/8ac69a4c-2cb1-477c-9135-678195f9c9f7">

- ## Quais são os principais componentes da ferramenta
  * Os resources do kubernetes já têm soluções ali implementadas para determinadas tipos de caso. Então nós temos, por exemplo: pods, ReplicaSets, Deployments, Volumes.
  * Então, por exemplo: se eu quero lidar com a questão de persistência de dados eu posso utilizar um recurso já pronto, que é o Persistent Volume. Então, se eu quero e devo utilizar e encapsular um container para utilizar no Kubernetes, eu utilizo um pod.
  * Utilizando esses recursos nós conseguimos construir aplicações bem elaboradas; onde, por exemplo, nós recebemos um tráfego de dados no nosso session, no nosso serviço e ele consegue fazer o balanceamento de cargas entre os pods que nós temos dentro da nossa aplicação.
  * Esses pods podem estar sendo gerenciados por um ReplicaSet que pode estar sendo gerenciado por um deployment e pode ser escalado. Nós podemos aumentar o número de pods, um horizontal pod autoscaler.
  <img width="987" alt="Screen Shot 2023-07-24 at 7 05 49 PM" src="https://github.com/DyaneAraujo/estudo_kubernetes/assets/114944655/6a812e0c-e8ba-48c7-aeb6-cee85915524d">
  
- ## O que é, e para o que serve a API
  * A API, além de receber as ordens do mundo externo e do que nós queremos fazer com o nosso cluster, ela é responsável por manter a comunicação com Controller Manager, um ETCD, com Scheduler e também os nossos nodes. Então através dela nós conseguimos criar um pod, editar um ReplicaSet, ler os dados no Deployment, deletar um Volume - tudo isso através da API, nós nunca vamos nos comunicar diretamente com os outros componentes; vai ser sempre através da API.

   ![image](https://github.com/DyaneAraujo/estudo_kubernetes/assets/114944655/1dc36309-0fe9-45f4-b366-9ac396556808)

- ## O que é, e para o que serve o kubectl
* O Kubectl, que nos provê as funcionalidades de criar, ler, atualizar e remover os dados do nosso cluster, os componentes do nosso cluster, os nossos recursos.
* Então, através do Kubectl nós conseguimos fazer isso de maneira declarativa ou imperativa. Nós podemos criar arquivos de definição, ou executarmos comandos, que simplesmente vão fazer essa mágica acontecer.
* E tudo isso ainda vai ser enviado um request do nosso Kubectl para a nossa API REST, que vai fazer a mágica acontecer dentro do nosso cluster.
