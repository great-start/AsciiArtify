**ArgoCD**

### Iнструмент для безперервного постачання (Continuous Delivery), який дає змогу автоматизувати розгортання та оновлення додатків у Kubernetes. Pеалізує підхід GitOps використовуючи репозиторій Git як джерело істини для визначення бажаного стану програми. Слідкує за змінами в репозирії та втягує зміни в кластер кубернетес (pull).

Маніфести Kubernetes можна вказувати кількома способами:

> kustomize applications
> helm charts
> jsonnet files
> Plain directory of YAML/json manifests

### Install

https://argo-cd.readthedocs.io/en/stable/#quick-start

### Access The Argo CD API Server¶

https://argo-cd.readthedocs.io/en/stable/getting_started/#3-access-the-argo-cd-api-server

### Отримаємо доступ до інтерфейсу ArgoCD GUI Отримати доступ можна в два шляхи:

> Service Type Load Balancer
> Ingress
> Port Forwarding

### Port Forwarding за допомогою локального порта 8080. В команді ми посилаємось на сервіс svc/argocd-server який знаходиться в namespace (-n argocd). Kubectl автоматично знайде endpoint сервісу та встановить переадресацію портів з локального порту 8080 на віддалений 443

$ kubectl port-forward svc/argocd-server -n argocd 8080:443&

### ArgoCD за замовчуванням працює з https тому при спробі відкрити 127.0.0.1:8080 ми отримаємо помилку сертифікати. Отже в продуктивній системі потрібно встановлювати сертифікати та налаштовувати ці моменти.

### Получение пароля (base64 закодований пароль) у певному форматі (-o jsonpath="{.data.password}")

$ kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"

### Використаємо команду base64 -d для повернення паролю в простий текст. Отриманий пароль та логін admin вводимо в Web-інтерфейс ArgoCD

$ kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

### Створимо додаток за допомогою графічного інтерфейсу.

### Тепер налаштовані в ArgoCD додатки будуть автоматично встановлюватись на оновлятись в Kubernetes.

### В розділі DESTINATION вкажемо url локального кластеру та Namespace demo після чого ArgoCD автоматично визначить параметри додатку використавши маніфести, які знаходяться в репозиторії. В разі бажання змінити значення вручну можна змінити іх значення в розділі PARAMETERS.

### У розділі політика синхронізація вкажемо як додаток буде синхронізуватись з репозиторієм. Тут важливо вказати ArgoCD щоб створив новий namespace так як в helm цю функцію за замовчуванням прибрали. Ставимо галку напроти AUTO-CREATE NAMESPACE

### Перевіряємо роботу застосунку.

$ kubectl port-forward -n <ns_name> svc/<svc_name> 8088:80

### в іншому вікні терміналу зробимо запит на вказаний порт та отримаємо відповідь у вигляді версії додатку:

$ curl localhost:8081
