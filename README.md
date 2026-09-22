# Verificación Automatizada de Pedidos Contra Entrega (COD)

Sistema de verificación de pedidos contra entrega para un negocio de e-commerce, construido en n8n (self-hosted) con Notion como memoria, OpenAI para clasificación e interpretación, Telegram para toda la comunicación con el cliente, y Gmail/Slack para el punto de revisión humana (HITL) y alertas técnicas.

Entrega Final — curso AI Automation, Comisión #96930.

## Enlaces del proyecto

- **Base de Datos en modo lectura (Notion):** https://app.notion.com/p/Verificaci-n-Automatizada-de-Pedidos-Contra-Entrega-3d8f420e9c5f80f0b65eda540c7c2da5?source=copy_link
- **Dashboard de Control (panel público):** https://app.notion.com/p/Dashboard-de-Control-Resumen-3ddf420e9c5f80ceb114d69ed1b16a79

## Archivos

- [`Diagrama_Arquitectura.pdf`](Diagrama_Arquitectura.pdf): informe completo (9 páginas): contexto, mapa de arquitectura, estructuras de datos, optimización de costos, seguridad y resiliencia, dashboard de control.
- [`workflow.json`](workflow.json): lógica completa del flujo, exportada de n8n (109 nodos, 174 conexiones).

## Evidencia del flujo en funcionamiento

- **Canvas General**

![Canvas General](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/728457139bf66b38cb8f1045ee3afd62eba55fb6/1.%20Canvas%20General.png)

- **Confirmación Pedido Camino Feliz (1/2):**

![Confirmación Pedido Camino Feliz (1/2)](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/cd00edd96a6b26da137278af7ca308a1eecb145d/2.%20Confirmacio%CC%81n%20Pedido%20Camino%20Feliz%20(1%3A2).png)

- **Confirmación Pedido Camino Feliz (2/2):**

![Confirmación Pedido Camino Feliz (2/2)](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/cd00edd96a6b26da137278af7ca308a1eecb145d/3.%20Confirmacio%CC%81n%20Pedido%20Camino%20Feliz%20(2%3A2).png)

- **Confirmación Pedido con Dirección Modificada Validada (1/2):**

![Confirmación Pedido con Dirección Modificada Validada (1/2)](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/cd00edd96a6b26da137278af7ca308a1eecb145d/4.%20Confirmacio%CC%81n%20Pedido%20con%20Direccio%CC%81n%20Modificada%20Validada%20(1%3A2).png)

- **Confirmación Pedido con Dirección Modificada Validada (2/2):**

![onfirmación Pedido con Dirección Modificada Validada (2/2)](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/cd00edd96a6b26da137278af7ca308a1eecb145d/5.%20Confirmacio%CC%81n%20Pedido%20con%20Direccio%CC%81n%20Modificada%20Validada%20(2%3A2).png)

- **Confirmación Pedido con HITL (Dirección Pedido Sospechosa) (1/3)**

![Confirmación Pedido con HITL (Dirección Pedido Sospechosa) (1/3)](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/210447d68f8e329022cba3a1e74459bce7dc99de/6.%20Confirmacio%CC%81n%20Pedido%20con%20HITL%20(Direccio%CC%81n%20Pedido%20Sospechosa)%20(1%3A3).png)

- **Confirmación Pedido con HITL (Dirección Pedido Sospechosa) (2/3)**

![Confirmación Pedido con HITL (Dirección Pedido Sospechosa) (2/3)](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/210447d68f8e329022cba3a1e74459bce7dc99de/7.%20Confirmacio%CC%81n%20Pedido%20con%20HITL%20(Direccio%CC%81n%20Pedido%20Sospechosa)%20(2%3A3).png)

- **Confirmación Pedido con HITL (Dirección Pedido Sospechosa) (3/3)**
  
![Confirmación Pedido con HITL (Dirección Pedido Sospechosa) (3/3)](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/210447d68f8e329022cba3a1e74459bce7dc99de/8.%20Cancelacio%CC%81n%20Pedido%20con%20HITL%20(Direccio%CC%81n%20Pedido%20Sospechosa)%20(3%3A3).png)

- **Cancelación Pedido por No Confirmación del Comprador en 24 hrs.**
  
![Cancelación Pedido por No Confirmación del Comprador en 24 hrs.](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/210447d68f8e329022cba3a1e74459bce7dc99de/9.%20Cancelacio%CC%81n%20Pedido%20por%20No%20Confirmacio%CC%81n%20del%20Comprador%20en%2024%20hrs.png)

- **Dashboard de Control**
  
![Dashboard de Control](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/210447d68f8e329022cba3a1e74459bce7dc99de/10.%20Dashboard%20de%20Control.png)
  

## Stack

n8n · Notion · OpenAI (gpt-4o-mini) · Telegram · Slack · Gmail · Google Address Validation API
