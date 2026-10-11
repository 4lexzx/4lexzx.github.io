# 4lexzx.github.io

Raíz del dominio `4lexzx.github.io`.

## Qué hay aquí

Solo hay un archivo, y no es para leer:

```
.well-known/assetlinks.json
```

Es la **verificación de la app de Préstamos** para Android (Digital Asset
Links). Le dice al teléfono que el APK `com.lexzx.prestamos` es el dueño
legítimo de este dominio.

### Por qué tiene que estar en la raíz

Android busca el archivo exactamente en:

```
https://4lexzx.github.io/.well-known/assetlinks.json
```

No admite atajos. Un repo de proyecto (como `Prestamos-S-U`) se publica bajo
`/Prestamos-S-U/`, así que no puede servirlo. Por eso hace falta este repo,
cuyo nombre coincide con el propio dominio.

### Qué pasa si se borra

La app de Préstamos seguirá funcionando, pero Android dejará de confiar en el
dominio y **volverá a mostrar la barra del navegador** dentro de la app.
Para recuperarlo basta con volver a subir el archivo.

### Si se regenera la clave de firma del APK

El archivo incluye la huella SHA-256 del certificado con el que está firmado
el APK. Si se vuelve a firmar con otra clave, hay que actualizar esa huella o
Android volverá a no confiar. La huella se saca con:

```
keytool -list -v -keystore android-keystore.keystore -alias android
```

## Publicación

Se publica con GitHub Pages (**Settings → Pages → Source: GitHub Actions**)
a través del workflow `.github/workflows/pages.yml`, que se lanza en cada
push a `main`.
