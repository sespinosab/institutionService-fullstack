1. Colocar las siguientes variables de entorno en la carpeta del backend: \
        DATABASE_URL="postgresql://postgres:1848@secretary-db:5432/institutiondb?schema=public"
        API_PORT=3333
        JWT_SECRET="secret-key" 
        BASE_URL="api"
        CORS_ORIGIN="http://materias-institucion-front:5172"

2. Colocar las siguientes variables de entorno en la carpeta del frontend:\
        VITE_API_URL="http://172.18.0.3:3333"
        VITE_API_PORT="3333"
        VITE_APP_HOST=0.0.0.0
        VITE_APP_PORT=5172\
    En caso de fallo, para VITE_API_URL inspeccionar el container del backend (docker inspect <backend_container_id>) y poner la url respectiva.

3. Sobre la carpeta raíz poner el siguiente comando en la terminal para desplegar los servicios: \
    docker-compose up --build

4. Revisar en los logs del container (docker logs <backend_container_id>) del backend la confirmación de que las migraciones de la DB han sido aplicadas.\

5. Ejecutar la semilla de la DB:\
    Entrar a la consola del container del backend: \
        docker exec -it <backend_container_id> sh\

    Ejecutar el siguiente comando.\
        npx prisma db seed\

    El siguiente mensaje debería aparecer en consola:\
        "Your database has been seeded."\

6. Ahora se puede entrar a la aplicación con estas credenciales por default:\
    Email: secretary@gmail.com 
    Constraseña: secretaria2