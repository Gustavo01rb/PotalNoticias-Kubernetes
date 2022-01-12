# Guia de instalação

- ### Configuação de IP
    Digite o seguinte comando:    
    ~~~
        kubectl get nodes -o wide
    ~~~
    Copie o IP interno do seu node "minikube" e o adicione no arquivo: /Config/configMap-portal.yaml. Obs: não altere a porta, somente o IP.

- ### Criação dos configMaps

    ~~~
    kubectl apply -f configMap-database.yaml && kubectl apply -f configMap-sistema.yaml && kubectl apply -f configMap-portal.yaml
    ~~~

- ### Criação dos Services

    ~~~
    kubectl apply -f service-database.yaml && kubectl apply -f service-portal.yaml && kubectl apply -f service-sistema.yaml
    ~~~

- ### Criação dos Deployments
    ~~~
    kubectl apply -f deploy-database.yaml && kubectl apply -f deploy-portal.yaml
    ~~~

- ### Criação dos persistent volume claim
    ~~~
    kubectl apply -f pvc-imagens.yaml && kubectl apply -f pvc-sessao.yaml 
    ~~~

- ### Criação dos persistent volume claim
    ~~~
    kubectl apply -f stfset-sistema.yaml 
    ~~~

## Testando a aplicação na web

- ### Obtenção da url de acesso
    Digite o comando   
    ~~~
    minikube service portal-svc --url
    ~~~
    E acesse a url retornada em seu navegador

- ### Usuário e senha
    ~~~
        Usuário: admin
        Senha: admin
    ~~~

## Comando único de criação

    ~~~
    kubectl apply -f configMap-database.yaml && kubectl apply -f configMap-sistema.yaml && kubectl apply -f configMap-portal.yaml && kubectl apply -f service-database.yaml && kubectl apply -f service-portal.yaml && kubectl apply -f service-sistema.yaml && kubectl apply -f deploy-database.yaml && kubectl apply -f deploy-portal.yaml && kubectl apply -f pvc-imagens.yaml && kubectl apply -f pvc-sessao.yaml && kubectl apply -f stfset-sistema.yaml 
    ~~~

obs: Aguarde alguns segundos após a criação

## Comando para deletar tudo
<b>Esse comando irá deletar outros deployments, services, configmaps, volumes claim e statefulSet caso existam.</b>

    ~~~
    kubectl delete statefulSet --all && kubectl delete PersistentVolumeClaim --all && kubectl delete configMaps --all &&  kubectl delete svc --all && kubectl delete deploy --all
    ~~~
