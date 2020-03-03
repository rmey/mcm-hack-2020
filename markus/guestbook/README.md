# Guestbook Sample

To deploy the guestbook application create two helm charts

```
> helm package gbapp
Successfully packaged chart and saved it to: ../guestbook/gbapp-0.1.0.tgz

> helm package gbchn
Successfully packaged chart and saved it to: ../guestbook/gbchn-0.1.0.tgz
```

Create the required namespaces on the hub-cluster
```
> oc new-project entitlement
> oc new project guestbook
```

Deploy the application via helm CLI

```
helm install gbchn -n devchn –namespace entitlement –tls

helm install gbapp -n gbapp –namespace guestbook –set channel.name=devchn,channel.namespace=entitlement –tls
```
## OR

Upload the charts to the MCM hub-cluster

```
> cloudctl login -a <hub-cluster-url> -u admin -p password

> cloudctl catalog load-chart --archive gbchn-0.1.0.tgz
Helm-Diagramm wird geladen
Helm-Diagramm wurde geladen

Diagramme im Repository 'local-charts' synchronisieren
OK

> cloudctl catalog load-chart --archive gbapp-0.1.0.tgz
Helm-Diagramm wird geladen
Helm-Diagramm wurde geladen

Diagramme im Repository 'local-charts' synchronisieren
OK
```

Deploy the chart from the MCM Catalog
- Select the catalog icon on the upper right
- Search for gbchn, select configure and fill in the parameters

| parameter | value       |
|-----------|-------------|
| name      | devchn      |
| namespace | entitlement |

- Search for gbapp, select configure and fill in the parameters

| parameter         | value       |
|-------------------|-------------|
| name              | gbapp       |
| namespace         | guestbook   |
| channel.name      | devchn      |
| channel.namespace | entitlement |

Check your application under Application Management