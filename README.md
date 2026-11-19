<!doctype html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Infraestructura E-commerce: Caso Zara</title>
<meta name="author" content="Tu Nombre">
<meta name="description" content="TP 2: Infraestructura por etapas usando 18 herramientas reales aplicadas a la marca Zara.">
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap">
<style>
/* DISEÑO POR ETAPAS (ACORDEONES) */
:root{
  --bg:#f8fafc; --surface:#ffffff; --ink:#0f172a; --muted:#64748b; --line:#e2e8f0;
  --primary:#2563eb; --primary-bg:#eff6ff; --accent:#ea580c; --accent-bg:#fff7ed;
  --stage-1:#059669; --stage-2:#d97706; --stage-3:#7c3aed; --stage-4:#db2777;
  --f-display:"Inter",system-ui,sans-serif;
  --f-mono:"JetBrains Mono",monospace;
}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){
  --bg:#0f172a; --surface:#1e293b; --ink:#f1f5f9; --muted:#94a3b8; --line:#334155;
  --primary:#60a5fa; --primary-bg:#1e3a8a; --accent:#fb923c; --accent-bg:#431407;
  --stage-1:#34d399; --stage-2:#fbbf24; --stage-3:#a78bfa; --stage-4:#f472b6;
}}
*{box-sizing:border-box}
body{margin:0; background:var(--bg); color:var(--ink); font-family:var(--f-display); font-size:15px; line-height:1.6; padding:30px 20px 80px;}
.wrap{max-width:1100px; margin:0 auto; display:flex; flex-direction:column; gap:40px;}
h1,h2,h3{margin:0; line-height:1.2;}
h1{font-size:clamp(32px, 5vw, 48px); font-weight:700; letter-spacing:-0.02em;}
h2{font-size:26px; font-weight:700; border-bottom:2px solid var(--line); padding-bottom:10px;}
p{margin:0;}
.lede{color:var(--muted); font-size:18px; max-width:75ch;}

/* Etapas */
.stage-container{display:flex; flex-direction:column; gap:20px;}
.stage{border:1px solid var(--line); border-radius:12px; overflow:hidden; background:var(--surface); box-shadow:0 2px 4px rgba(0,0,0,0.02);}
.stage-header{padding:16px 20px; display:flex; align-items:center; gap:15px; cursor:pointer; user-select:none; background:var(--surface); transition:background 0.2s;}
.stage-header:hover{background:var(--bg);}
.stage-num{width:32px; height:32px; border-radius:50%; display:flex; align-items:center; justify-content:center; font-weight:700; color:white; font-family:var(--f-mono);}
.stage-title{font-size:18px; font-weight:600;}
.stage-content{padding:20px; border-top:1px solid var(--line); display:none; background:var(--bg);}
.stage.open .stage-content{display:block;}
.stage.open .stage-header{background:var(--bg); border-bottom:1px solid var(--line);}

/* Tarjetas de Herramientas */
.tools-grid{display:grid; grid-template-columns:repeat(auto-fit, minmax(300px, 1fr)); gap:16px;}
.tool-card{background:var(--surface); border:1px solid var(--line); border-radius:8px; padding:16px; display:flex; flex-direction:column; gap:10px; position:relative;}
.tool-header{display:flex; justify-content:space-between; align-items:flex-start;}
.tool-name{font-size:16px; font-weight:700; color:var(--primary);}
.tool-concept{font-family:var(--f-mono); font-size:11px; background:var(--primary-bg); color:var(--primary); padding:2px 6px; border-radius:4px; border:1px solid var(--primary);}
.tool-desc{font-size:14px; color:var(--ink);}
.tool-meta{font-size:12px; color:var(--muted); font-style:italic; margin-top:auto;}

/* Tablas */
.table-wrap{overflow-x:auto; background:var(--surface); border:1px solid var(--line); border-radius:10px;}
table{border-collapse:collapse; width:100%; font-size:14px;}
th,td{text-align:left; padding:12px 16px; border-bottom:1px solid var(--line);}
th{background:var(--bg); font-weight:600; color:var(--muted); text-transform:uppercase; font-size:12px; letter-spacing:0.05em;}
tr:last-child td{border-bottom:0;}

/* Cajas de Código */
pre{background:#1e293b; color:#e2e8f0; padding:14px; border-radius:8px; overflow-x:auto; font-family:var(--f-mono); font-size:13px; line-height:1.5;}

/* Ajustes móviles */
@media (max-width: 600px) {
  .stage-header{flex-direction:column; align-items:flex-start; gap:10px;}
  .tools-grid{grid-template-columns:1fr;}
}
</style>
</head>
<body>

<div class="wrap">
  <header>
    <h1>Infraestructura Digital: El caso de Zara</h1>
    <p class="lede">Análisis de la arquitectura de una tienda de moda global. Vemos cómo Zara sostiene millones de visitas y picos de tráfico (como los lanzamientos de rebajas) usando <strong>18 herramientas y conceptos clave</strong> divididos en 4 etapas.</p>
  </header>

  <div class="stage-container" id="stages">
    <!-- ETAPA 1 -->
    <div class="stage">
      <div class="stage-header">
        <div class="stage-num" style="background:var(--stage-1)">1</div>
        <div class="stage-title">Desarrollo, CI/CD e Infraestructura como Código</div>
      </div>
      <div class="stage-content">
        <p style="margin-bottom:15px; color:var(--muted); font-size:14px;">Los equipos de Zara (Inditex) despliegan cientos de actualizaciones a la semana. Aquí es donde el código se escribe, se prueba y se sube a los servidores sin intervención manual.</p>
        <div class="tools-grid">
          <div class="tool-card">
            <div class="tool-header"><span class="tool-name">GitHub Actions</span><span class="tool-concept">#2 IaC (Infraestructura como Código)</span></div>
            <div class="tool-desc">Cada vez que un programador de Zara sube un cambio en el diseño de la web, este sistema ejecuta pruebas automáticas y publica la nueva versión sin afectar a los usuarios.</div>
            <div class="tool-meta">Automatiza todo el ciclo de vida</div>
          </div>
          <div class="tool-card">
            <div class="tool-header"><span class="tool-name">Docker</span><span class="tool-concept">#6 Graceful Shutdown</span></div>
            <div class="tool-desc">Zara empaqueta su sistema de ventas en contenedores. Si un servidor necesita reiniciarse en medio de una ola de compras, Docker le avisa al sistema para que termine de procesar los pagos en curso antes de apagarse.</div>
            <div class="tool-meta">Evita cortar compras a medias</div>
          </div>
          <div class="tool-card">
            <div class="tool-header"><span class="tool-name">Kubernetes (K8s)</span><span class="tool-concept">#14 LB + UUID</span></div>
            <div class="tool-desc">Orquesta los contenedores. Cuando Zara lanza su colección de invierno, el tráfico se multiplica. Kubernetes clona automáticamente los servidores para aguantar la demanda y les asigna IPs dinámicas.</div>
            <div class="tool-meta">Escalabilidad elástica</div>
          </div>
        </div>
      </div>
    </div>

    <!-- ETAPA 2 -->
    <div class="stage">
      <div class="stage-header">
        <div class="stage-num" style="background:var(--stage-2)">2</div>
        <div class="stage-title">Entrada, Red y Tráfico (El Edge)</div>
      </div>
      <div class="stage-content">
        <p style="margin-bottom:15px; color:var(--muted); font-size:14px;">Cómo los millones de clientes de Zara llegan a los servidores y cómo se les entrega las fotos de las prendas al instante.</p>
        <div class="tools-grid">
          <div class="tool-card">
            <div class="tool-header"><span class="tool-name">Cloudflare DNS</span><span class="tool-concept">#9 LB vs Gateway</span></div>
            <div class="tool-desc">Resuelve la dirección web (zara.com). Si el centro de datos de Europa se satura, Cloudflare redirige a los usuarios europeos al centro de datos de Estados Unidos automáticamente.</div>
            <div class="tool-meta">Balanceo geográfico (GeoDNS)</div>
          </div>
          <div class="tool-card">
            <div class="tool-header"><span class="tool-name">Nginx</span><span class="tool-concept">#17 Proxy Inverso</span></div>
            <div class="tool-desc">Recibe las peticiones HTTPS. Se encarga de entregar la página web inicial (HTML/CSS) y deriva las peticiones de "buscar prenda" o "pagar" al sistema interno.</div>
            <div class="tool-meta">También actúa como Load Balancer (#9)</div>
          </div>
          <div class="tool-card">
            <div class="tool-header"><span class="tool-name">Kong API Gateway</span><span class="tool-concept">#4 API Gateway</span></div>
            <div class="tool-desc">El "guardián" de la tienda. Verifica que el usuario tenga su sesión activa antes de dejarlo ver su historial de pedidos o pasar al pago. Si un bot intenta raspar el catálogo, lo bloquea.</div>
            <div class="tool-meta">Seguridad y Rate Limiting</div>
          </div>
          <div class="tool-card">
            <div class="tool-header"><span class="tool-name">CloudFront (AWS CDN)</span><span class="tool-concept">#3 CDN</span></div>
            <div class="tool-desc">Zara tiene miles de fotos en altísima resolución. Esta red de distribución guarda copias de las fotos en servidores cerca del cliente, para que la página cargue en milisegundos.</div>
            <div class="tool-meta">Descongestiona los servidores centrales</div>
          </div>
        </div>
      </div>
    </div>

    <!-- ETAPA 3 -->
    <div class="stage">
      <div class="stage-header">
        <div class="stage-num" style="background:var(--stage-3)">3</div>
        <div class="stage-title">Microservicios (La Lógica de Moda)</div>
      </div>
      <div class="stage-content">
        <p style="margin-bottom:15px; color:var(--muted); font-size:14px;">Cada parte de la tienda (Catálogo, Pagos, Cuentas) es un sistema independiente. Si falla el sistema de recomendaciones, los clientes aún pueden pagar.</p>
        <div class="tools-grid">
          <div class="tool-card">
            <div class="tool-header"><span class="tool-name">Node.js (Catálogo)</span><span class="tool-concept">#19 Redis / Caché</span></div>
            <div class="tool-desc">Servicio que muestra los productos. Si pides ver la "Campera Puffer", primero busca en la memoria rápida (Redis); si no está, va a la base de datos lenta.</div>
            <div class="tool-meta">Frontend API</div>
          </div>
          <div class="tool-card">
            <div class="tool-header"><span class="tool-name">Auth0 / OAuth2</span><span class="tool-concept">#11 OAuth 2.0</span></div>
            <div class="tool-desc">El servicio de Zara ID. Permite que los usuarios inicien sesión usando su cuenta de Google o Facebook, sin necesidad de crear una contraseña nueva para Zara.</div>
            <div class="tool-meta">Identidad Federada</div>
          </div>
          <div class="tool-card">
            <div class="tool-header"><span class="tool-name">Stripe / Adyen</span><span class="tool-concept">#1 Webhooks</span></div>
            <div class="tool-desc">La pasarela de pago. Cuando el banco del cliente aprueba la compra, Stripe envía un "Webhook" (un mensaje invisible) a Zara para avisar que el pago se completó y preparar el envío.</div>
            <div class="tool-meta">Zara nunca ve la tarjeta de crédito</div>
          </div>
          <div class="tool-card">
            <div class="tool-header"><span class="tool-name">Java (Servicio de Pedidos)</span><span class="tool-concept">#13 Secuencia vs UUID</span></div>
            <div class="tool-desc">Gestiona el carrito. Cuando compras, te asigna un número de orden correlativo (ej. ORD-88421) usando una secuencia de base de datos. Es más fácil para atención al cliente buscar un número corto que un código UUID gigante.</div>
            <div class="tool-meta">Generación de IDs</div>
          </div>
        </div>
      </div>
    </div>

    <!-- ETAPA 4 -->
    <div class="stage">
      <div class="stage-header">
        <div class="stage-num" style="background:var(--stage-4)">4</div>
        <div class="stage-title">Datos, Caché y Procesos Asíncronos</div>
      </div>
      <div class="stage-content">
        <p style="margin-bottom:15px; color:var(--muted); font-size:14px;">Donde la información de stock y los pedidos se guardan de forma segura, y donde se procesan las tareas lentas (como enviar correos) sin bloquear al cliente.</p>
        <div class="tools-grid">
          <div class="tool-card">
            <div class="tool-header"><span class="tool-name">PostgreSQL</span><span class="tool-concept">#18 Connection Pool</span></div>
            <div class="tool-desc">Base de datos principal de stock. Si hay un pico de ventas, se conecta mediante un "Pool" de conexiones para que el servidor no se sature al recibir miles de consultas a la vez.</div>
            <div class="tool-meta">Consistencia de stock (ACID)</div>
          </div>
          <div class="tool-card">
            <div class="tool-header"><span class="tool-name">Redis</span><span class="tool-concept">#7 Session vs JWT</span></div>
            <div class="tool-desc">Guarda la sesión del usuario y su carrito. Si el usuario cierra sesión, el carrito se borra de Redis al instante. También guarda la lista de los productos más vistos para cargar la home en 0.1 segundos.</div>
            <div class="tool-meta">Caché de alta velocidad</div>
          </div>
          <div class="tool-card">
            <div class="tool-header"><span class="tool-name">RabbitMQ</span><span class="tool-concept">#15 Colas Async</span></div>
            <div class="tool-desc">Cuando el cliente hace clic en "Comprar", Zara no lo hace esperar a que se envíe el correo. El pedido entra en esta cola y un proceso en segundo plano se encarga de enviar el email de confirmación.</div>
            <div class="tool-meta">Tareas en background</div>
          </div>
          <div class="tool-card">
            <div class="tool-header"><span class="tool-name">Apache Kafka</span><span class="tool-concept">#5 Kafka / Eventos</span></div>
            <div class="tool-desc">Registra "eventos" (ej: "se vendió una camisa azul talle M"). Múltiples equipos de Zara leen este flujo: el equipo de logística para reponer stock, y el equipo de marketing para actualizar las tendencias de moda.</div>
            <div class="tool-meta">Flujo de eventos masivo</div>
          </div>
          <div class="tool-card">
            <div class="tool-header"><span class="tool-name">Amazon S3</span><span class="tool-concept">#16 Presigned URL</span></div>
            <div class="tool-desc">Almacena los videos de las pasarelas de Zara. Para que un usuario vea un video privado o un fotógrafo suba imágenes, S3 genera una URL firmada que expira en pocos minutos.</div>
            <div class="tool-meta">Almacenamiento seguro</div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- SECCIÓN DE PREGUNTAS / COMPARACIONES -->
  <section>
    <h2>¿Por qué Zara elige estas herramientas? (Comparaciones del TP)</h2>
    <div class="table-wrap">
      <table>
        <thead><tr><th>Concepto</th><th>Elección para Zara</th><th>Justificación de la marca</th></tr></thead>
        <tbody>
          <tr>
            <td>Session vs JWT</td>
            <td><strong>Session (Redis)</strong> para la web pública.</td>
            <td>Zara necesita poder cerrar sesión de forma inmediata si detecta actividad sospechosa (como un bot comprando todas las prendas de una colección limitada). Un JWT no se puede revocar fácilmente.</td>
          </tr>
          <tr>
            <td>Secuencia vs UUID</td>
            <td><strong>Secuencia</strong> para Pedidos y <strong>UUID</strong> para productos.</td>
            <td>Los clientes se comunican con el número de pedido (ej. #90012) para consultar por su envío. Los productos usan UUID porque se crean a diario en distintos países sin necesidad de coordinar un número único global.</td>
          </tr>
          <tr>
            <td>Colas vs Kafka</td>
            <td><strong>Cola (RabbitMQ)</strong> para emails de "tu pedido ha salido" y <strong>Kafka</strong> para el análisis de ventas global.</td>
            <td>El email es una tarea única para un usuario. Pero cuando se vende una prenda en Madrid, Zara necesita actualizar el stock en Tokio, calcular tendencias en tiempo real y ajustar la producción. Eso lo hace Kafka.</td>
          </tr>
          <tr>
            <td>LB vs API Gateway</td>
            <td><strong>Ambos:</strong> Nginx (LB) y Kong (Gateway).</td>
            <td>Zara recibe picos brutales cuando lanza las rebajas. El Load Balancer distribuye la carga física. El Gateway evita que la web colapse limitando cuántas compras puede intentar hacer un solo usuario por minuto.</td>
          </tr>
        </tbody>
      </table>
    </div>
  </section>

  <!-- SECCIÓN DE EJEMPLOS DE CÓDIGO -->
  <section>
    <h2>Ejemplo técnico: El momento exacto de la compra en Zara</h2>
    <div class="tools-grid">
      <div class="tool-card">
        <div class="tool-header"><span class="tool-name">Petición de Compra (API Checkout)</span></div>
        <pre>POST /api/v1/zara/checkout
Authorization: Bearer &lt;JWT&gt;
Idempotency-Key: "usr-992a-compra-01"

{
  "items": [
    {"sku": "ZR-7781-M", "qty": 1, "price": 49.90},
    {"sku": "ZR-1022-L", "qty": 1, "price": 29.90}
  ],
  "total": 79.80,
  "currency": "EUR"
}</pre>
        <div class="tool-desc">La <em>Idempotency-Key</em> evita que, si el usuario tiene mala señal y toca "Comprar" dos veces, Zara le cobre dos veces la misma campera.</div>
      </div>
      <div class="tool-card">
        <div class="tool-header"><span class="tool-name">Evento enviado a Kafka (por detrás)</span></div>
        <pre>Topic: "ventas-globales"
Key: "ZR-7781-M"

{
  "evento": "prenda_vendida",
  "pais": "ES",
  "tienda": "online",
  "timestamp": "2026-11-05T22:45:00Z"
}</pre>
        <div class="tool-desc">Mientras el usuario ve la pantalla de "Gracias por tu compra", este mensaje viaja por Kafka para que los sistemas de logística de Inditex preparen la caja y el envío.</div>
      </div>
    </div>
  </section>

</div>

<script>
  // Lógica para abrir y cerrar las etapas (Acordeón)
  document.querySelectorAll('.stage-header').forEach(header => {
    header.addEventListener('click', () => {
      const stage = header.parentElement;
      stage.classList.toggle('open');
    });
  });

  // Abrir la primera etapa por defecto
  document.querySelector('.stage').classList.add('open');
</script>
</body>
</html>
