#+title: Kubernetes Local Setup
#+author: Jimmie Fulton

* Kubernetes Local Setup
  
** K3d setup

* [[https://doc.traefik.io/traefik/getting-started/install-traefik/][Install Traefik]]

#+NAME: traefik-dashboard.yml
#+FILENAME: traefik-dashboard.yml 
#+begin_src yaml
---
apiVersion: traefik.containo.us/v1alpha1
kind: IngressRoute
metadata:
  name: dashboard
spec:
  entryPoints:
    - web
  routes:
    - match: Host(`traefik.test`) && (PathPrefix(`/dashboard`) || PathPrefix(`/api`))
      kind: Rule
      services:
        - name: api@internal
          kind: TraefikService
#+end_src

#+begin_src sh
kubectl apply -f dashboard.yml
#+end_src

