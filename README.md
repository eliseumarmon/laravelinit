# Iniciar proyecto de Laravel rápido

1. Clonar repositorio
2. En terminal ejecutar `docker compose up --build`
3. Borrar archivo .empty de src
4. Entrar en contenedor de php `docker compose exec -it php bash`
   * Crear proyecto Laravel `composer create-project laravel/laravel .`
5. Configurar MySQL
   * Configurar fichero .env

        ```config
            DB_CONNECTION=mysql
            DB_HOST=127.0.0.1
            DB_PORT=3306
            DB_DATABASE=laravel
            DB_USERNAME=alumno
            DB_PASSWORD=alumno
        ```

> [!WARNING]
>
> Si Laravel no encuentra la tabla sessions:
>
> 1. Entramos en el contenedor de php. `docker compose exec -it php bash`
> 2. Es posible que tengamos que hacer `php artisan session:table` (puede que ya exista)
> 3. Realizar una migración inicial: `php artisan migrate`

---

> [!WARNING]
>
> Si Laravel lanza error `No application encryption key has been specified`:
>
> 1. Asegurarnos de que existe el fichero .env en la raíz del proyecto
> 2. Si no existe lo creamos y configuramos a partir de .env.example (el archivo se crea al iniciar proyecto en laravel)
> 3. En el contenedor de php (`docker compose exec -it php bash`): ejecutamos `php artisan key:generate`
