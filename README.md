# Proyecto 2 - WordPress persistente

Aplicacion WordPress y MySQL 8 con datos persistentes, red privada y arranque condicionado por salud de la base de datos.

## Ejecutar

```sh
cp .env.example .env
# Edite .env y reemplace las claves de ejemplo.
docker compose up -d
docker compose ps
docker volume ls
```

Abra `http://localhost:8080`, complete la instalacion y publique una entrada de prueba. Para demostrar persistencia, ejecute `docker compose down`, luego `docker compose up -d`: la entrada seguira disponible porque los volumenes nombrados conservan MySQL y `wp-content`.

## Preguntas

- `docker compose down -v` elimina tambien los volumenes y por tanto los datos; uselo con cuidado.
- WordPress usa `db` porque Compose ofrece DNS interno por nombre de servicio; una IP puede cambiar.
- El healthcheck comprueba que MySQL acepta conexiones. Un `depends_on` simple solo ordena el inicio, no espera que el servicio este listo.

## Evidencias pendientes de capturar

Agregue en `evidencias/` capturas de la entrada antes y despues de `docker compose down`, y de `docker volume ls`.
