# Sistema de Aprobación de Préstamos con IA 🤖💰

[Imagen principal del proyecto: Un gráfico de barras que muestre la cantidad de préstamos aprobados vs. rechazados]

## Descripción del Proyecto

Este proyecto innovador utiliza inteligencia artificial (IA) para automatizar y agilizar el proceso de aprobación de préstamos. Al analizar datos clave de los clientes, nuestro modelo de aprendizaje automático predice la probabilidad de que un cliente cumpla con sus pagos, lo que permite tomar decisiones de préstamo más rápidas y precisas.

## Características Destacadas

*   **Modelo de IA Robusto:** Nuestro modelo de aprendizaje automático, basado en un Perceptron, ha sido entrenado con datos históricos de préstamos, lo que garantiza predicciones confiables.
*   **Arquitectura de Microservicios:** El sistema está diseñado con microservicios (generador de datos, balanceador de carga y aplicación de IA) para una mayor escalabilidad y mantenimiento.
*   **Contenerización con Docker:** Cada microservicio se ejecuta en un contenedor Docker, lo que facilita la implementación y la portabilidad en diferentes entornos.
*   **Orquestación con Kubernetes (Opcional):** Para entornos de producción, puedes utilizar Kubernetes para gestionar y escalar automáticamente los microservicios.

## Cómo Funciona

1.  **Generación de Datos:** El componente `gen` extrae datos de clientes relevantes (edad, ingresos, puntuación crediticia, etc.) de una base de datos PostgreSQL.
2.  **Balanceo de Carga:** El `loadbalancer`, implementado con Nginx, distribuye los datos de los clientes entre varias instancias de la aplicación de IA para un procesamiento eficiente.
3.  **Predicción de Aprobación:** Las instancias de la aplicación `iapp` utilizan el modelo de IA para evaluar los datos y predecir si se debe aprobar o rechazar el préstamo.
4.  **Actualización de la Base de Datos:** Los resultados de las predicciones se almacenan en la base de datos, lo que permite un seguimiento y análisis posterior.

## Demostración

[Imagen o GIF del sistema en acción]

## Instrucciones de Implementación (Minikube)

1.  **Clona este repositorio:** `git clone https://github.com/<tu_usuario>/<tu_repositorio>.git`
2.  **Inicia Minikube:** `minikube start`
3.  **Despliega los componentes:**
    ```bash
    kubectl apply -f kubernetes/postgresql-pvc.yaml
    kubectl apply -f kubernetes/postgresql-deployment.yaml
    kubectl apply -f kubernetes/postgresql-service.yaml
    kubectl apply -f kubernetes/loadbalancer-service.yaml
    kubectl apply -f kubernetes/gen-deployment.yaml
    kubectl apply -f kubernetes/gen-service.yaml
    kubectl apply -f kubernetes/iapp-deployment.yaml
    kubectl apply -f kubernetes/iapp-service.yaml
    ```
4.  **Accede a la aplicación:** Encuentra la IP del servicio y el puerto en los que se expone la aplicación.

## Próximos Pasos

*   **Integración con Istio:** Mejora la gestión del tráfico, la seguridad y la observabilidad con Istio.
*   **Monitorización:** Añade herramientas de monitorización para supervisar el rendimiento y la salud del sistema.
*   **Optimización del Modelo:** Experimenta con diferentes algoritmos y técnicas de ajuste para mejorar la precisión del modelo de IA.

## Contribuciones

¡Las contribuciones son bienvenidas! Si tienes ideas para mejorar el proyecto, abre un issue o envía un pull request.
