# Estrutura de Deploy Kafka com Kustomize + GitOps

Este repositório organiza os manifests do **Kafka** e componentes relacionados utilizando **Kustomize**.

---

## 📂 Estrutura do Repositório

# TREE
```
├── kafka
│ ├── base # Manifestos base do cluster Kafka
│ └── overlays
│ ├── dev # Customizações específicas DEV
│ └── uat # Customizações específicas UAT
│
├── operator
│ ├── base # Instalação do Operator
│ └── overlays
│ ├── dev
│ └── uat
│
├── project
│ ├── base # Definição do namespace Kafka
│ └── overlays
│ ├── dev
│ └── uat
│
└── README.md # Este arquivo
```

## 📌 Ordem Recomendada de Deploy

project → cria o namespace

operator → instala o Strimzi Operator

kafka → provisiona o cluster Kafka


## 🚀 Deploy com Kustomize

### DEV
```bash
oc apply -k project/overlays/dev
oc apply -k operator/overlays/dev
oc apply -k kafka/overlays/dev
```

### UAT
```bash
oc apply -k project/overlays/uat
oc apply -k operator/overlays/uat
oc apply -k kafka/overlays/uat
```


