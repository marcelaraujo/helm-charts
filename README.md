# Helm charts repository

This repository folder works as an helm charts package repository, containing the helm spec `index.yaml` file in it's root and packages in the `charts` folder.  

```
$ helm repo add marcelaraujo https://marcelaraujo.github.io/helm-charts
$ helm update
```

# Publishing a chart 

Assuming that you have a ready to use chart in the `src` folder that you want to make available, you can ran the following commands:

```
$ helm package --destination ./helm-charts/ ./src/MyAwesomeChart
$ helm repo index --url https://marcelaraujo.github.io/helm-charts/ .
```

**Publishing Signed packages**

Helm chart packages can be signed with a pgp key, this is an optional step but it adds trust to your chart.

To publish and generate a signed package you should basically follow the instructions above but pass the --sign option to the package command:

```
helm package --destination ./helm-charts/ src/webencryptor/ --sign --key "key id" --keyring ~/.gnupg/secring.gpg 
```

Refer to this [link](https://helm.sh/docs/developing_charts/#the-workflow) for more detailed instructions.

