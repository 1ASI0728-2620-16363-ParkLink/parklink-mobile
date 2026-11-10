# Aplicación móvil

Aplicación Flutter de ParkLink para buscar estacionamientos, gestionar reservas y administrar la cuenta.

## Responsabilidades

- Ofrece un mapa, búsqueda, reservas, perfil y asistente conversacional.
- Se comunica con la pasarela y carga los mosaicos de OpenStreetMap.
- Incluye código heredado de transporte; el punto de entrada de ParkLink es lib/main.dart.

## Tecnologías

Flutter, Dart y flutter_map.

## Arquitectura C4

El diagrama muestra una **vista de contenedores C4** centrada en este componente y sus relaciones relevantes. Se genera desde [Structurizr DSL](docs/architecture/workspace.dsl) con los estilos predeterminados, sin colores personalizados. Las flechas indican la dirección de cada interacción. El diagrama se conserva en inglés.

![Diagrama C4 de Aplicación móvil](docs/architecture/containers.svg)

Para consultar o regenerar el diagrama, abra `docs/architecture/workspace.dsl` en Structurizr. Con Structurizr CLI y Graphviz instalados:

```sh
structurizr.sh validate -workspace docs/architecture/workspace.dsl
mkdir -p /tmp/parklink-diagram
structurizr.sh export -workspace docs/architecture/workspace.dsl -format dot -output /tmp/parklink-diagram
dot -Tsvg /tmp/parklink-diagram/structurizr-Containers.dot -o docs/architecture/containers.svg
```

## Ejecución local

```sh
flutter pub get
flutter run --dart-define=PARKLINK_API_URL=http://localhost:3000
flutter test
```

Para el emulador de Android, use `10.0.2.2` en lugar de `localhost`. Los archivos de configuración de Firebase y las credenciales de firma no se incluyen; proporcione los suyos cuando sean necesarios. Las funciones heredadas de Google Maps requieren una clave restringida `GOOGLE_MAPS_API_KEY` mediante `--dart-define`.

## Relación con el proyecto

Este repositorio es la fuente de la aplicación móvil. El backend, el panel web y la infraestructura local están en [parklink-platform](https://github.com/1ASI0728-2620-16363-ParkLink/parklink-platform). El código móvil se mantiene aquí, no en el espacio integrado.
