# Verificación Automatizada de Pedidos Contra Entrega (COD)

Sistema de verificación de pedidos contra entrega para un negocio de e-commerce, construido en n8n (self-hosted) con Notion como memoria, OpenAI para clasificación e interpretación, Telegram para toda la comunicación con el cliente, y Gmail/Slack para el punto de revisión humana (HITL) y alertas técnicas.

Entrega Final — curso AI Automation, Comisión #96930.



## Enlaces del proyecto


- **Base de Datos en modo lectura (Notion):** https://app.notion.com/p/Verificaci-n-Automatizada-de-Pedidos-Contra-Entrega-3d8f420e9c5f80f0b65eda540c7c2da5?source=copy_link
- **Dashboard de Control (panel público):** https://app.notion.com/p/Dashboard-de-Control-Resumen-3ddf420e9c5f80ceb114d69ed1b16a79


## Archivos


- [`Diagrama_Arquitectura.pdf`](Diagrama_Arquitectura.pdf): Informe completo (9 páginas): contexto, mapa de arquitectura, estructuras de datos, optimización de costos, seguridad y resiliencia, dashboard de control.
- [`workflow.json`](workflow.json): Lógica completa del flujo, exportada de n8n (111 nodos, 176 conexiones).


## Stack


![n8n](https://img.shields.io/badge/n8n-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)
![Notion](https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI%20(gpt--4o--mini)-412991?style=for-the-badge&logo=openai&logoColor=white)
![Telegram](https://img.shields.io/badge/Telegram-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)
![Slack](https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=slack&logoColor=white)
![Gmail](https://img.shields.io/badge/Gmail-EA4335?style=for-the-badge&logo=gmail&logoColor=white)
![Google Address Validation API](https://img.shields.io/badge/Google%20Address%20Validation%20API-4285F4?style=for-the-badge&logo=google&logoColor=white)




## Evidencia del flujo en funcionamiento


- **Canvas General:**

Canvas completo de n8n con los 111 nodos del workflow, organizados en las 8 secciones del proceso (Verificación y Motor de Riesgo, Cascada de Confirmación, Rama Telegram, Cascada de Dirección Corregida, Registro y Mensajes Finales, Revisión Humana, Manejo de Errores y Reporte Diario). Confirma que el sistema documentado en el PDF existe realmente en n8n, con la misma cantidad de nodos y conexiones.


![Canvas General](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/728457139bf66b38cb8f1045ee3afd62eba55fb6/1.%20Canvas%20General.png)


- **Confirmación Pedido Camino Feliz (1/2: Trigger Pedido Nuevo Ingresado):**

Un pedido con dirección válida y comprador de buen historial recorre el flujo completo sin intervención manual: el cliente recibe el mensaje inicial por Telegram, presiona "CONFIRMAR PEDIDO", y el sistema responde con el mensaje real de despacho una vez validada la dirección. La fila en Notion (Centro de Comando) queda con Estado "Confirmó" y Dirección Validada "TRUE". 


![Confirmación Pedido Camino Feliz (1/2)](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/cd00edd96a6b26da137278af7ca308a1eecb145d/2.%20Confirmacio%CC%81n%20Pedido%20Camino%20Feliz%20(1%3A2).png)


- **Confirmación Pedido Camino Feliz (2/2: Trigger:

Botón Presionado Comprador):** Un pedido con dirección válida y comprador de buen historial recorre el flujo completo sin intervención manual: el cliente recibe el mensaje inicial por Telegram, presiona "CONFIRMAR PEDIDO", y el sistema responde con el mensaje real de despacho una vez validada la dirección. La fila en Notion (Centro de Comando) queda con Estado "Confirmó" y Dirección Validada "TRUE". La captura muestra la ejecución correspondiente en n8n, de punta a punta y sin errores.


![Confirmación Pedido Camino Feliz (2/2)](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/cd00edd96a6b26da137278af7ca308a1eecb145d/3.%20Confirmacio%CC%81n%20Pedido%20Camino%20Feliz%20(2%3A2).png)


- **Confirmación Pedido con Dirección Modificada Validada (1/2):**

El cliente presiona "Modificar dirección", el sistema le pide que escriba la corrección por texto libre, y al recibirla la revalida en vivo contra Google Address Validation antes de confirmar el pedido. Demuestra la cascada de corrección de dirección funcionando de extremo a extremo, incluyendo la interpretación de la respuesta del cliente con IA.


![Confirmación Pedido con Dirección Modificada Validada (1/2)](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/cd00edd96a6b26da137278af7ca308a1eecb145d/4.%20Confirmacio%CC%81n%20Pedido%20con%20Direccio%CC%81n%20Modificada%20Validada%20(1%3A2).png)


- **Confirmación Pedido con Dirección Modificada Validada (2/2):**

El cliente presiona "Modificar dirección", el sistema le pide que escriba la corrección por texto libre, y al recibirla la revalida en vivo contra Google Address Validation antes de confirmar el pedido. Demuestra la cascada de corrección de dirección funcionando de extremo a extremo, incluyendo la interpretación de la respuesta del cliente con IA. La captura muestra la ejecución real en n8n de este camino.


![onfirmación Pedido con Dirección Modificada Validada (2/2)](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/cd00edd96a6b26da137278af7ca308a1eecb145d/5.%20Confirmacio%CC%81n%20Pedido%20con%20Direccio%CC%81n%20Modificada%20Validada%20(2%3A2).png)


- **Confirmación Pedido con HITL (Dirección Pedido Sospechosa) (1/3):**

Escalamiento a Revisión Humana (HITL) por dirección sospechosa Google Address Validation marca la dirección del pedido como no confirmable, y el sistema escala automáticamente a Revisión Humana: llega un correo a Gmail con el detalle del pedido y dos botones, "Aprobar" y "Rechazar", sin que el operador necesite abrir n8n ni Notion. 


![Confirmación Pedido con HITL (Dirección Pedido Sospechosa) (1/3)](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/210447d68f8e329022cba3a1e74459bce7dc99de/6.%20Confirmacio%CC%81n%20Pedido%20con%20HITL%20(Direccio%CC%81n%20Pedido%20Sospechosa)%20(1%3A3).png)


- **Confirmación Pedido con HITL (Dirección Pedido Sospechosa) (2/3):**

Escalamiento a Revisión Humana (HITL) por dirección sospechosa Google Address Validation marca la dirección del pedido como no confirmable, y el sistema escala automáticamente a Revisión Humana: llega un correo a Gmail con el detalle del pedido y dos botones, "Aprobar" y "Rechazar", sin que el operador necesite abrir n8n ni Notion. 


![Confirmación Pedido con HITL (Dirección Pedido Sospechosa) (2/3)](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/210447d68f8e329022cba3a1e74459bce7dc99de/7.%20Confirmacio%CC%81n%20Pedido%20con%20HITL%20(Direccio%CC%81n%20Pedido%20Sospechosa)%20(2%3A3).png)


- **Cancelación Pedido con HITL (Dirección Pedido Sospechosa) (3/3):**

Rechazo desde HITL El operador presiona "Rechazar" en el correo de Revisión Humana; el sistema cancela el pedido automáticamente, registra el motivo ("Rechazo manual - revisión humana") en Notion, y le envía al cliente el mensaje de cancelación por Telegram — cierra el ciclo de HITL sin que nadie tenga que tocar n8n directamente.

  
![Cancelación Pedido con HITL (Dirección Pedido Sospechosa) (3/3)](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/210447d68f8e329022cba3a1e74459bce7dc99de/8.%20Cancelacio%CC%81n%20Pedido%20con%20HITL%20(Direccio%CC%81n%20Pedido%20Sospechosa)%20(3%3A3).png)


- **Cancelación Pedido por No Confirmación del Comprador en 24 hrs.:**

El cliente nunca responde al mensaje inicial: el sistema manda un recordatorio a la 1h y otro a las 7h, avisando cuántas horas quedan antes de que el pedido se cancele solo. Al cumplirse las 24h sin respuesta, el pedido se cancela automáticamente con el motivo "Cliente no confirmó a tiempo", sin intervención humana — evidencia del Test de Estrés sobre la cascada de espera.

  
![Cancelación Pedido por No Confirmación del Comprador en 24 hrs.](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/210447d68f8e329022cba3a1e74459bce7dc99de/9.%20Cancelacio%CC%81n%20Pedido%20por%20No%20Confirmacio%CC%81n%20del%20Comprador%20en%2024%20hrs.png)


- **Dashboard de Control:**

Dashboard de Control Panel de KPIs en Notion, alimentado automáticamente por el reporte diario: gráfico de tiempo de respuesta promedio por integración (Notion, Telegram, OpenAI, Gmail, Google), tabla de KPIs de sistema (tasa de error, reintentos, errores del día) y tabla de KPIs de negocio (volumen, efectividad, tasa de cancelación, causa raíz), con vistas en vivo de los pedidos agrupados por estado.

  
![Dashboard de Control](https://github.com/jonvillarroelj-arch/AI_Automation_Entrega_Final_96930/blob/210447d68f8e329022cba3a1e74459bce7dc99de/10.%20Dashboard%20de%20Control.png)
  
