### ->  mediascope

вводные:

a. git; kubectl; flux

b. wg-cfg & kubeconfig

0:
github:
https://github.com/imsociable/apps-repo/
https://github.com/imsociable/infra-repo/

1. flux
<img width="1346" height="546" alt="image" src="https://github.com/user-attachments/assets/e55791ec-a93c-470e-9741-ff88f55893c4" />




2.
### infra-repo 
```
infra-repo/
├── clusters/
│   └── infra/
│       ├── flux-system/
│       │   ├── gotk-components.yaml
│       │   ├── gotk-sync.yaml
│       │   └── kustomization.yaml
│       ├── apps-repo-source.yaml
│       └── apps-kustomization.yaml
└── README.md
```
### apps-repo
```
apps-repo/
├── apps/
│   └── podinfo/
│       ├── deployment.yaml
│       ├── hpa.yaml
│       ├── kustomization.yaml
│       ├── namespace.yaml
│       └── service.yaml
└── README.md
```
(взял из podinfo/kustomize/ с добавлением namespace)

3.
 - убедился в работоспособности Flux:
 
 a:
 
<img width="823" height="69" alt="image" src="https://github.com/user-attachments/assets/90b8863b-85d5-4a79-8508-b4ee86a1d0bd" />

 b:
 
 <img width="652" height="94" alt="image" src="https://github.com/user-attachments/assets/0fe36c78-a9fe-4669-aa06-ad9272967179" />



 - в моём случае для проверки podinfo в web использовал следующий port-forward:
```
kubectl --kubeconfig=.\kubeconfig.yaml port-forward -n podinfo deployment/podinfo 8080:9898
```

URL:
```
http://localhost:8080/
```

4. намеренно изменил image-tag на невалидный, получив следующий ответ:
<img width="621" height="145" alt="image" src="https://github.com/user-attachments/assets/0a939929-a816-4098-a1fd-e066903a4b74" />

вернулся на предыдущий, явно рабочий коммит с помощью:
```
git revert HEAD && git push origin main
```

статус нормализовался

<img width="418" height="47" alt="image" src="https://github.com/user-attachments/assets/00dcc085-5bef-4961-aef0-07738e2775ea" />

