# Caja de herramientas de marketing analytics (WebMCP)

Sitio estático de un solo archivo, sin build. Calculadoras de métricas de campaña,
LTV/CAC, UTMs, significancia A/B y tamaño de muestra, expuestas como herramientas WebMCP.

## Desplegar en Netlify
- Rápido: arrastra esta carpeta a https://app.netlify.com/drop
- CLI: `netlify deploy --prod --dir .`
- Git: sube la carpeta a un repo e impórtalo en Netlify (sin comando de build, publica la raíz).

## Herramientas expuestas
Imperativas (JavaScript): calcular_metricas_campana, calcular_ltv_cac,
evaluar_prueba_ab, calcular_tamano_muestra_ab.
Declarativa (formulario HTML): construir_utm.
Memoria de sesión (sin backend, sin API keys): resumen_sesion devuelve todo
lo calculado hasta el momento en el navegador, para que el agente compare o
combine resultados entre herramientas (ej. ROAS vs. LTV/CAC) usando su propio
razonamiento, no uno de este sitio.

## Probar con un agente
Activa chrome://flags/#enable-webmcp-testing. Sin la flag, la página usa un shim local
y la consola del agente funciona igual. Cada llamada hace
dataLayer.push({event: "webmcp_tool_call", ...}), listo para GTM.

## Para agregar una calculadora
Escribe la función de cálculo, su vista y una entrada en el arreglo HERRAMIENTAS;
el registro en WebMCP y el formulario quedan conectados automáticamente.
