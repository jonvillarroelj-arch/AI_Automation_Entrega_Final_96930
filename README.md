# Verificación Automatizada de Pedidos Contra Entrega (COD)

Sistema de verificación de pedidos contra entrega para un negocio de e-commerce, construido en n8n (self-hosted) con Notion como memoria, OpenAI para clasificación e interpretación, Telegram para toda la comunicación con el cliente, y Gmail/Slack para el punto de revisión humana (HITL) y alertas técnicas.

Entrega Final — curso AI Automation, Comisión #96930.

## Enlaces del proyecto

- **Base de Datos en modo lectura (Notion):** https://app.notion.com/p/Verificaci-n-Automatizada-de-Pedidos-Contra-Entrega-3d8f420e9c5f80f0b65eda540c7c2da5?source=copy_link
- **Dashboard de Control (panel público):** https://app.notion.com/p/Dashboard-de-Control-Resumen-3ddf420e9c5f80ceb114d69ed1b16a79

## Archivos

- `Diagrama_Arquitectura.pdf` — informe completo (9 páginas): contexto, mapa de arquitectura, estructuras de datos, optimización de costos, seguridad y resiliencia, dashboard de control.
- `workflow.json` — lógica completa del flujo, exportada de n8n (109 nodos, 174 conexiones).
- `screenshots/` — evidencia del flujo funcionando en la práctica.

## Evidencia del flujo en funcionamiento

*(agregar aquí las imágenes a medida que se suban a `screenshots/`, por ejemplo:)*

```
![Vista general del canvas](screenshots/canvas-general.png)
![Sección 1 - Verificación y Riesgo](screenshots/seccion1-verificacion-riesgo.png)
![Ejecución camino feliz](screenshots/execution-camino-feliz.png)
![Ejecución camino infeliz](screenshots/execution-camino-infeliz.png)
![Mensaje real en Telegram](screenshots/telegram-mensaje-cliente.png)
![Correo HITL con botones Aprobar/Rechazar](screenshots/hitl-correo-aprobar-rechazar.png)
```

## Stack

n8n · Notion · OpenAI (gpt-4o-mini) · Telegram · Slack · Gmail · Google Address Validation API
