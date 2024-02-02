# Kubernetes
[ doc - kubernetes](https://kubernetes.io/docs/concepts/workloads/pods/)

### services:
> Pod -> 1: { Container: 1, Container: 2 }

> Pod -> 2: { Container: 1, Container: 2 }

### minikube:
> minikube cria um cluster com apenas 1 node contendo os componentes do Master Node e do Worker Node.

> Utilziado para configuração base do kubernetes, ótima ferramenta de estudo.

> Com minikube podemos criar um container com ambiente kubernetes.

> para crair um cluster com minikube basta executar ``minikube start`` e ara deletar ``minikube start``.

> criar container com o nome chamado nginx com imagem do nginx ``kubectl run nginx --image nginx`` ex: kubectl run nome-do-POD --image nome-da-imagem, para mais infos adicionar: ``-o wide``.


[doc - install - mac](https://minikube.sigs.k8s.io/docs/)

> O kubernetes faz acesso ao POD e não a container
> 

    kubernetes cluster {
        Node: [
            POD: {
                container
            }
            POD: {
                container
            }
        ]
    }

### POD:

> POD em Kubernetes é a menor unidade de computação publicável em um computador que podemos criar e gerencias

### kubectl

> Buscar a os PODs criados ``kubectl get pods``.

> Pegar descriçnao do POD ``kubectl describe pod nginx``.

> Fazemos use do kubectl para criar PODs no nosso cluster
``kubectl run nginx --image nginx``.

> Para criar um pode através do de um YAML podemos utilizar ``create -f nome-do-arquivo.yaml``.




# Objetivo: 
    

### Geral: 
 > Estudo cloud -> devops

> Iniciou seus serviços em 2008 ->  ficou conehcida mundialmente em 2013
        
>GCP - Google Cloud Plataform

> Localizações:

    3 zonas: 
        exemplo:
        Multi-Region{
            US: {
                Europe: {
                    europe-west2: {
                        zona: {
                            europe-west2-a: {
                                data-centers
                            }
                            europe-west2-b: {
                                data-centers
                            }
                            europe-west2-C: {
                                data-centers
                            }
                        }
                    }
                }
            }
        }

### Organização da conta GCP:

    ORGANIZATION - Company: {
        Dept Y: {
            Team A
            Team B: {
                Product_1: {
                    DEV GCP Project: {
                        MICROSERVICES
                    },
                    Test GCP Project:
                    Production GCP Project:
                }
            }
        },
        Dept X
        Shared
    }

### YAML:
> A configuração de YAML para kubernetes precisa ter algumas proprides:

> OBS: Não devemos utilizar tab para identar o arquivo, para YAML é utilizado dois espaços.

    apiVersion: v1
    Kind: Pod
    metadata:
        name: nome-do-pod
        labels:
            app: nome-da-app

    spec:

> O arquivo YAML pode ser criado pelo kubectl ``kubectl create -f nome-do-arquivo-yaml``

### Replication Controller -> ReplicaSets:
> Responsável fazer uma replica exata de um pod em execução, além disso ele certica que o número especificado de pods do cluster estejam sendo executados.

> O ReplicaSets é uma versão mais atualizada do Replication Controller.

> A escolha entre ReplicationController e ReplicaSets pode ser feita na chave ``kind`` do yaml.

> A configuração do POD a ser replicado deve ser feita no ``spec``

    spec: {
        template:{},
        spec: {},
        replicas: 2
        }
        Selector
> Nesse caso deve ter ao menos dois PODs em execução.

> Um diferença entre o ReplicationController e o ReplicaSets é que no apiVersion o valor é v1 ja no ReplicaSet o valor é apps/v1.

> O campo Selector indica, dentre os PODs existentes qual deve ser utilizado para replicação no cluter, no ReplicaSet o Selector é obrigatório e no ReplicationController é opcional.

> É possível criar um um ReplicaSets para tipos diferentes de PODS's dentro de um mesmo cluster, para isso é necessário aidiconar a chave label para identificação dos POD's


## habilitando uma organização:

> IAM 
    Identity 
    Seguir passo a passo de configuração da organização solicitada pela Google...

> Manage Resources
    Podemos configiurar os folders,
    configurar nome do projeto, 
    criar folders...

> Billing:  15
    Criar relatórios de billings por projetos e outroas coisas referente a gastos.

    Cost Table:
        Da para verificar por utilização separadamente de cada microserviço, além disso é possível verificar os dados de acordo com cada projeto.

budgets & alerts:  16
    Tava de seguraça para custos

cloudshell
SDK - Kit de Desenvolvimento de Software
Então resumidamente a GCLOUD é um kit de desenvolvimento de software, no caso quando executamos via shell
executar "gcloud" -> visualiza todas as opções disponibilizadas pela google no shell
exmplo de comando: 
    gcloud compute instances list
    gcloud: comando
    compute: o serviço
    no serviço: instances
    e o que quero fazer: list

Dentro do gcloud ainda tem o gsutil
que nos permite fazer mais algumas coisas 

Available commands:
  acl              Get, set, or change bucket and/or object ACLs
  autoclass        Configure Autoclass feature
  bucketpolicyonly Configure uniform bucket-level access
  cat              Concatenate object content to stdout
  compose          Concatenate a sequence of objects into a new composite object.
  config           Obtain credentials and create configuration file
  cors             Get or set a CORS JSON document for one or more buckets
  cp               Copy files and objects
  defacl           Get, set, or change default ACL on buckets
  defstorageclass  Get or set the default storage class on buckets
  du               Display object size usage
  hash             Calculate file hashes
  help             Get help about commands and topics
  hmac             CRUD operations on service account HMAC keys.
  iam              Get, set, or change bucket and/or object IAM permissions.
  kms              Configure Cloud KMS encryption
  label            Get, set, or change the label configuration of a bucket.
  lifecycle        Get or set lifecycle configuration for a bucket
  logging          Configure or retrieve logging on buckets
  ls               List providers, buckets, or objects
  mb               Make buckets
  mv               Move/rename objects
  notification     Configure object change notification
  pap              Configure public access prevention
  perfdiag         Run performance diagnostic
  rb               Remove buckets
  requesterpays    Enable or disable requester pays for one or more buckets
  retention        Provides utilities to interact with Retention Policy feature.
  rewrite          Rewrite objects
  rm               Remove objects
  rpo              Configure replication
  rsync            Synchronize content of two buckets/directories
  setmeta          Set metadata on already uploaded objects
  signurl          Create a signed URL
  stat             Display object status
  test             Run gsutil unit/integration tests (for developers)
  ubla             Configure Uniform bucket-level access
  update           Update to the latest gsutil release
  version          Print version info about gsutil
  versioning       Enable or suspend versioning for one or more buckets
  web              Set a website configuration for a bucket

Additional help topics:
  acls             Working With Access Control Lists
  crc32c           CRC32C and Installing crcmod
  creds            Credential Types Supporting Various Use Cases
  dev              Contributing Code to gsutil
  encoding         Filename encoding and interoperability problems
  metadata         Working With Object Metadata
  naming           Object and Bucket Naming
  options          Global Command Line Options
  prod             Scripting Production Transfers
  security         Security and Privacy Considerations
  shim             Shim for Running gcloud storage
  support          Google Cloud Storage Support
  versions         Object Versioning and Concurrency Control

Storage: 21
    existem algumas classes para acessar cada tipo de arqui, por exemplo:
    Standard Storage serve para uma grande quantidade de acesso como um vídeo.

    Nearline Storage: custo menor, no entanto é para quem pretende guardar dados por pelomenos 30 dias

    coldline Storage: é um tipo de armazenamento que vai permanecer por pelo menos 90 dias.

    Archive Storage: custo muito baixo.Para arquivos que não podem ser jogados fora, mas que caso seja necessários eles estão guardados.

    Nessas 3 opções quanto mais barato o armazenamento mais caro fica a leitura e gravação, isso se deve ao tipo de armazenamento utilizado pela google para que alguns dos serviços fiquem mais baros no entanto com maior dificuldade de acesso.
    
bucket:
    protection: 
        Em proteção é possível adionar uma polita de retenção, nele é possível adicionar um tempo minimo de retação, muito bom para guardar backups, garantido assim que os arquivos não sejam removidos.

        é possivel adiconar um lock para que essa politica não seja removida.

    Lifecycle:
        No bucket é possível definir o Lifecyclo dos dos itens, um emxeplo seria, caso alguém queira fazer o backup de seus itens no entanto existem arquivos que são diarimente utilizados e outros em meses ou mais, é possivel criar regras para alterar a classe de armazenamento, assim conseguimos reduzir custos.
        
        É possível criar regra para remover o item tbm de acordo com a regra criada.
        
        Nesse caso é uma otima escolha para redução de custos de storage, criar boas regras de lifecyclo.

Organização:
    IAM:
        É possível criar grupos que tem acessos e regras para determinadas funções 

        Members: 
            Posso criar meus usuários
        Roles:
            O que os members podem fazer e que tipo de serviço eles podem acessar 

            é possível criar uma role com permissões especificas, Roles fica dentro de IAM & Admin
        

Compute Engine 
    AutoScaling:
        Escolonamento automatico de acordo com a regra aplica. ex: utilização de 70%...
    
    AutoHealing:
        É possivel criar um perfil de healt check que verifica se aplicação esta funcionando de acordo com uma regra que podemos adicionar, e recuperar-la em caso de problema, exemplo, ao fazer uma requisição ela demorou mais que 5sg para responder, pomos informar q nesse caso signifca que esta com problema...

        É necessário adicionar o AutoHealing na instancia do compute engine

Load Balancer:
    É responsável por gerenciar o autoscaling da nossa aplicação, controlando o IP externo dos nossos ips internet 

temp - service on:
    instance template -> template das minhas VMs
    instance group - > Configuração de um grupo de VMs, escalonamentos etc.
    healt check

LoadBalance:
    Gerenciador de uso da aplicação, é possível fazer controle de trefego de dados, controle de usuario -> servers 
    CDN -> Faz o controle de uso por região, envia as requisições para os servidores mais proximos por exemplo.
    
VPC - Virtual Private Cloud
    ip .1 sempre vai ser o gateway dentro da VPC
    
    classe ip privadas: 
    A = 10.0.0.0 - 10.255.255.255 -> /8
    B = 172.16.0.0 - 172.31.255.255 -> /12
    C = 192.168.0.0 - 192.168.255.255 -> /16
    restantes são público

    VPC - network
        É possível configurar redes vistuais, inserindo VMs e provavelmente outras coisas dentro dessa rede.

        OBS: Primeiro criamos nossa VPC, após isso podemos criar nossas VMs informando na aba network qual VPC queremos utilizar e nossa subnet caso exista.

    Image exemple: https://cloud.google.com/resource-manager/docs/cloud-platform-resource-hierarchy?hl=pt-br

    OBS: Nesses casos é possível separar os billing entre essas pastasl

links:
Free Services: https://cloud.google.com/products
Gcloud cervices: https://cloud.google.com/?utm_source=google&utm_medium=cpc&utm_campaign=latam-BR-all-pt-dr-BKWS-all-all-trial-p-dr-1605194-LUAC0014411&utm_content=text-ad-none-any-DEV_c-CRE_512285710752-ADGP_Hybrid%20%7C%20BKWS%20-%20PHR%20%7C%20Txt%20~%20GCP_General-KWID_43700062788251482-kwd-464643078222&utm_term=KW_gcloud-ST_Gcloud&gclid=Cj0KCQjwmZejBhC_ARIsAGhCqneNpdTEpXEYgAk3lVWQKOCdiwxGweC8Rj38GxEhJzNYIuCV_rUAqeQaApS4EALw_wcB&gclsrc=aw.ds
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Insalações:
    NodeJS: https://nodejs.org/en/ 
    cmder: https://cmder.net/
    Pacotes: pesquisar pactes do Node https://www.npmjs.com/search?q=express

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Comandos:
    node -v: Verificar versão do NodeJS.
    npm -v: Verificar versão do NPM.
    npm install: Reinstala todos os pacotes baseado no package.json, caso a pasta node_modules seja exclida ou o projeto seja executado em outro equipamento.
    npm install --save-dev "pacote": Para instalar um pacote como dependencia dev.
    npm update: Atualiza todos os pacotes.
    npm update "pacote": Atualiza um pacote especifico.
    npx npm-check-updates -u: Verifica se tem algum dependencia que precisa de atualização
    npm run "scritp": Serve para executar scripts configurado no arquivo package.json.
    npm install -g "pacote": serve para instalar os pacotes de forma global.
        npm link "pacote": Em alguns casos é necessário executar o npm link "pacote" pois alguns pacotes necessita dos arquivos localmente.
    npm uninstall "pacote": Para remover os pacotes, ele remove as dependencias dos arquivos json também.
    node: acessa o node via terminal.
    nom install nodemon: Serve para atualizar auttomaticamente o servidor, lembrar de instalar em modo dev '--save-dev'

    npm init: inicializar o NPM no prjeto (permite instalar modulos externos).
        OBS: Lembrar de inicializar o projeto com 'npm init' antes.
     Pacotes NPM:
        npm install minimist: minimist é um pacote que permite extrair argumentos do console.
        npm install chalk: chalk é um pacote para uma visualização do console mais agradável.
            Correção - Para funcionar corretamente: npm install chalk@4.1.2
        npm install inquirer: Módulo para lidar melhor com input do usuário.
            Correção - Para funcionar corretamente: npm install inquirer@8.1.0
        npm install lodash: Verificar...(compara array)
        npm install express: responsavel po renderizar html, fazer conexão com banco entre outras coisas.
        npm install express-handlebars:




    OBS: 
        Para reparar basta trocar esta linha de código:
        app.engine('handlebars', exphbs())

        Por esta:
        app.engine('handlebars', exphbs.engine())

MongoDB: 
    busca de tabelas: show dbs

criar:
use 'nome'

insert:
    db.Fields.unsertOne({ name: 'anderson', age: 25})



criado Fields