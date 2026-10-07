# Pachamama · Sala de Control

Plataforma única que reúne el **tablero de Gerencia** (8 vistas del CRM) y el **dashboard de
Meta Ads de Marketing** (10 pestañas). Antes eran dos páginas en dos repositorios distintos.

## Qué hay en este repositorio

| Archivo | Qué es |
|---|---|
| `index.html` | La plataforma: menú de dos niveles, portada, una sola puerta de entrada y una sola clave de Gerencia |
| `tablero-gerencia.html` | El tablero de Gerencia, con los cambios acordados el 2026-10-07 |
| `dashboard-marketing.html` | El dashboard de Meta Ads v3.11.1, con los cambios acordados el 2026-10-07 |
| `datos/acceso.json` | La contraseña de entrada. **Hay que llenarla** |
| `datos/m2.json` | Los metros cuadrados obtenidos, que hoy se escriben a mano |
| `datos/reactivacion.json` | Las difusiones de WhatsApp, que se suben a mano como antes |
| `_parches/` | Los scripts que convirtieron los dos tableros originales en estas copias. No se publican; quedan para poder repetir el proceso |

## Antes de publicar

1. **Pon la contraseña** en `datos/acceso.json`, en el campo `clave`. Mientras diga
   `PON_AQUI_LA_CONTRASENA`, la puerta deja pasar a cualquiera y lo avisa en la portada.
2. Activa **GitHub Pages** en este repositorio, desde la rama principal, carpeta raíz.
3. Comprueba desde la dirección publicada que:
   - el puente de Meta responde (en una dirección local no responde: solo acepta los dominios
     de la empresa);
   - con la clave de Gerencia puesta, la portada muestra los cuatro números del CRM.

## Cómo funciona

- **La plataforma no mezcla el código de los dos tableros.** Cada uno sigue siendo su propio
  archivo y se abre dentro de un marco cuando entras a su área. Así no chocan entre ellos y
  solo se carga lo que miras.
- **La clave se pide una sola vez.** Los tres archivos viven en el mismo dominio, así que la
  clave de Gerencia que guardas en la plataforma la usan también los dos tableros.
- **Un solo reloj.** La plataforma refresca cada 2 minutos y solo el área que estás mirando.
  Los relojes propios de cada tablero quedaron subordinados a ese. Esto importa: Kommo bloquea
  por dirección IP y el servidor sale por la misma que reparte los leads.
- **Nada se precarga.** Entrar a la plataforma no consulta a Meta ni a Kommo; la portada pide
  tres datos y cada área pide los suyos al abrirse.

## Qué cambió respecto de los tableros originales

Decisiones tomadas el 2026-10-07 (artefacto de las 26 decisiones).

| Decisión | Qué se hizo |
|---|---|
| A1 · Embudo | El embudo de Gerencia cuenta a quien **llegó a esa etapa o más**. Un lead que hoy está en «No responde» o «Venta Perdido» ya no figura como si nunca hubiera avanzado: se usa su etapa anterior, que entrega `/api/perdidos` |
| A3 · Metas | Mandan las metas de Gerencia: Contactado 80%, Meet agendado 90%, Meet presentado 90%, Cliente 20%. Separación conserva la de Marketing porque Gerencia no tiene una |
| A6 · Costo por cliente | Se mantiene la fórmula: inversión con IGV entre los leads vendidos. Se agregó el **costo por cada 1000 m² obtenidos**, con los metros escritos a mano |
| A8 · Hora | Toda la plataforma corta el día en **hora de Lima**, también los rangos a medida. Antes el tablero de Gerencia usaba el reloj de cada computadora |
| C1 · Menú | Dos niveles: primero el área, dentro sus vistas |
| C2 · Inicio | Portada nueva con lo esencial de los dos |
| C3 · Estilo | Colores y tipografías de Marketing en toda la plataforma |
| C4 · Iconos | Se quitaron los 86 emojis del menú, los títulos y los botones |
| C6 · Nombre | «Pachamama · Sala de Control» |
| D2 · Reactivación | Entra igual que hoy, con el archivo a mano |
| E2 · Contraseña | Se mantiene, y la página dice con todas sus letras que **no es una medida de seguridad** |

## Lo que todavía falta

- **A2 · Dejar fuera del embudo los 1,297 leads de Evolta.** Se distinguen por la etiqueta
  `evolta-<año>`, que el puente de Cloudflare no deja pasar. Hace falta habilitarla; lo hace el
  dueño de la cuenta de Cloudflare.
- **C5 · Hora en el filtro de fechas de Marketing.** El tablero de Gerencia ya filtra por hora;
  el de Marketing todavía no.
- **D2 · Reactivación en vivo.** Pedido aparte a Italo: hace falta una ruta nueva en el servidor.
  También quedan por corregir dos textos de ayuda de esa pestaña que describen un cálculo viejo.
- **E1 · Clave de solo lectura.** Hoy una sola clave abre la lectura **y** la escritura del
  servidor: quien la tiene puede cambiar el reparto de leads. Se decidió asumir el riesgo por
  escrito y pedir la separación después. Debe quedar aprobado por Gerencia.
- **E3 · Aviso en los dos tableros viejos** que apunte a esta plataforma.

## Si algo sale mal

Los dos tableros originales siguen publicados y funcionando en sus direcciones de siempre:
`asistentegerencia-cpu.github.io/pachamama-tablero/` y
`marketing-pachamama.github.io/pachamama-marketing/dashboard-meta.html`.
Esta plataforma no los toca. Las copias originales del 2026-10-07 están guardadas en
`Fusion Tableros/respaldo-originales/`.
