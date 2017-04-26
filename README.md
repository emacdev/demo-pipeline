# demo-pipeline
CI as code

Using Jenkins and openshit for a jenkins build pipeline

# Command executed for build deploy promote

C:\bin\minishift-1.0.0-rc.2-windows-amd64
λ oc policy add-role-to-user edit system:serviceaccount:tg-pipeline:jenkins -n testing

C:\bin\minishift-1.0.0-rc.2-windows-amd64
λ oc policy add-role-to-user edit system:serviceaccount:tg-pipeline:jenkins -n development

C:\bin\minishift-1.0.0-rc.2-windows-amd64
λ oc policy add-role-to-group system:image-puller system:serviceaccounts:testing -n development

C:\bin\minishift-1.0.0-rc.2-windows-amd64
λ oc create deploymentconfig tgapp --image=172.30.1.1:5000/development/tgapp:promoteToTesting
deploymentconfig "tgapp" created
