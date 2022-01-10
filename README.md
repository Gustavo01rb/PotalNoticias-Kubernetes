kubectl apply -f configMap-database.yaml && kubectl apply -f configMap-sistema.yaml && kubectl apply -f configMap-portal.yaml

kubectl apply -f service-database.yaml && kubectl apply -f service-portal.yaml && kubectl apply -f service-sistema.yaml

kubectl apply -f deploy-database.yaml && kubectl apply -f deploy-portal.yaml

kubectl apply -f pvc-imagens.yaml && kubectl apply -f pvc-sessao.yaml 