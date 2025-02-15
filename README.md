### DFG GitOps with Kubernetes

Karena kita udah mendekati waktu workshop, ada beberapa prerequisites yg temen2 perlu setup dulu di laptop yg akan digunakan ketika workshop nanti.
1. Install terminal kalau belum punya
2. Install kubectl (https://kubernetes.io/docs/tasks/tools/)
3. Install fluxcd (https://fluxcd.io/flux/installation/)
4. Install docker. Kalau untuk linux bisa pakai docker-ce, kalau untuk windows dan mac bisa pakai docker dekstop

Selain itu temen2 juga perlu menyiapkan akun repository yg akan dipakai dalam workshop
1. Daftar akun dockerhub (https://hub.docker.com/)
2. Daftar github (https://github.com/)




##### How to 
1. create 2 token on docker hub
    - read only (for flux kub)
    - read write (for github runner)

2. setup Workflow for repo apps

3. setup repo-gitops

4. setup token github

5. ssh into controller kub
    run command: 
        - `export GITHUB_TOKEN=<your_token>`

        - `export KUBECONFIG=/etc/rancher/k3s/k3s.yaml`
        
        - `flux bootstrap github --hostname=github.com --token-auth --owner=ryoguritno --repository=DFG-GitOps --branch=master --personal --components-extra=image-reflector-controller image-automation-controller --interval 30s --verbose`
