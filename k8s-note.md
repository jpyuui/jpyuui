helmCharts:
- name: blackduck
  repo: https://sig-repo.synopsys.com/artifactory/sig-cloudnative
  version: 2022.10.1
  releaseName: bd-development
  namespace: bd
  valuesFile: values.yaml

kustomization.yaml

上記はkustomizationのhelm機能の使い方

apiVersion: argoproj.io/v1alpha1
kind: ApplicationSet

spec:
    template:
        source:
            plugin:
                name: kustomize-build-with-helm


argocd application自体もGitOpsを使えます

     helmfile --environment="$branch" sync && \
     sleep 10 && \
     kubectl apply -n argocd -k preboot/"$branch" ;


