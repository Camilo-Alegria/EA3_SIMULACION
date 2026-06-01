# Simulación del Sistema de Atención Bancaria

Este proyecto implementa un simulador de eventos discretos para un sistema de atención bancaria utilizando Python. El objetivo principal es evaluar el impacto de diferentes configuraciones de cajeros (mixtos y especializados) en la eficiencia operativa, el tiempo de espera de los usuarios y la utilización de los recursos del banco.

##  Autores
* **Fernando Beltrán**
* **Camilo Alegría**

---

## 📝 Descripción del Proyecto
El código simula la operación de una sucursal bancaria durante una jornada de trabajo (por defecto 480 minutos o 8 horas). Los clientes llegan de forma aleatoria buscando realizar dos tipos principales de operaciones: **Retiros** (70% de probabilidad) o **Pagos** (30% de probabilidad). 

Además, los usuarios se clasifican dinámicamente según su velocidad de transacción en cuatro categorías: **Rápido, Normal, Lento y Muy Lento**, lo que afecta directamente los tiempos de llegada y de servicio a través de distribuciones exponenciales parametrizadas.

### 📊 Escenarios Evaluados
El simulador analiza y compara de forma automática 4 configuraciones distintas de atención:
1. **`3_mixtos`**: Tres cajeros con capacidad de atender tanto retiros como pagos.
2. **`2_retiro_1_pago`**: Dos cajeros exclusivos para retiros y uno exclusivo para pagos.
3. **`1_retiro_2_pago`**: Un cajero exclusivo para retiros y dos exclusivos para pagos.
4. **`4_mixtos`**: Cuatro cajeros con capacidad de atender cualquier tipo de operación.

---

## 🚀 Características Clave
* **Simulación Basada en Eventos**: Control estricto del tiempo de simulación mediante una lista ordenada de eventos (`llegada` y `fin_servicio`).
* **Categorización de Usuarios**: Modelado probabilístico diferenciado para el comportamiento de clientes según su velocidad.
* **Múltiples Réplicas**: Ejecuta 10 réplicas por cada escenario con semillas aleatorias fijas (`np.random.seed`) para garantizar la estabilidad estadística del modelo.
* **Intervalos de Confianza**: Cálculo matemático de intervalos de confianza del 95% (IC95%) para las principales métricas del sistema.
* **Análisis de Balanceo**: Herramienta integrada para evaluar si la carga de trabajo entre cajeros está equilibrada o desbalanceada (umbral crítico del 30% de diferencia).

---

## 📉 Métricas Calculadas
El sistema recolecta datos exhaustivos en cada simulación, incluyendo:
* **Métricas de Rendimiento**: Clientes totales atendidos (desglosados por tipo de operación), tiempos promedio de espera en cola, tiempo promedio de servicio y tiempo total en el sistema.
* **Métricas de Teoría de Colas**:
  * $\lambda$ (Tasa promedio de llegada)
  * $\mu$ (Tasa promedio de servicio)
  * $\rho$ (Factor de utilización del sistema)
  * $L$ y $L_q$ (Número promedio de clientes en el sistema y en la cola)
  * $W$ y $W_q$ (Tiempo promedio de estancia en el sistema y en la cola)
* **Utilización Individual**: Porcentaje de ocupación exacto de cada cajero.

---

## 🛠️ Requisitos e Instalación

Para ejecutar este cuaderno de Jupyter (`.ipynb`), necesitas tener instalado Python 3 junto con las siguientes bibliotecas de análisis de datos y visualización:

```bash
pip install numpy pandas matplotlib
