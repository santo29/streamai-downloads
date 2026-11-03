# StreamAI Studio

Aplicación para Windows que transmite en vivo a varias plataformas a la vez e incluye un host de IA para el chat de Twitch.

[![Última versión](https://img.shields.io/github/v/release/santo29/streamai-downloads)](https://github.com/santo29/streamai-downloads/releases/latest)

StreamAI Studio es gratuito y de código cerrado. Este repositorio contiene los instaladores, las notas de cada versión y los términos de uso. El código fuente no es público.

## Descargas

| Plataforma | Requisitos | Enlace |
|---|---|---|
| Windows | Windows 10 u 11 de 64 bits | [StreamAI-Studio-Windows-Setup.exe](https://github.com/santo29/streamai-downloads/releases/latest/download/StreamAI-Studio-Windows-Setup.exe) |
| Android | Android 7.0 o superior | [StreamAI-Studio-Android.apk](https://github.com/santo29/streamai-downloads/releases/latest/download/StreamAI-Studio-Android.apk) |
| Navegador | Chrome recomendado | [streamai-studio-db.web.app](https://streamai-studio-db.web.app) |

La versión completa es la de Windows, porque incluye el motor de transmisión local con FFmpeg. La versión web y el APK sirven para probar el estudio, pero no transmiten a las plataformas ni responden el chat con IA. El APK no ha cambiado desde la versión 1.6.0.

## Problemas conocidos en la versión 1.8.2

Comprobados en noviembre de 2026 al probar la versión publicada. Están corregidos en el código de la próxima versión, que aún no se ha publicado:

- Host de IA en Kick: no recibe mensajes, porque Kick cambió su sistema de chat. En Twitch sí funciona.
- Coste de la IA: en un chat activo la app hace una llamada al proveedor por cada mensaje, sin límite, y puede agotar tu saldo rápido.
- Errores de la IA: si el proveedor rechaza la clave o no responde, la app no lo muestra.
- Google Gemini: el modelo predeterminado de la app ya no existe, así que no responde.
- Clonar Pantalla: se transmite sin el sonido del equipo, así que el juego no se oye.
- Clips automáticos: no arrancan. Al pulsar Inicializar Módulo aparece un aviso de error.
- Micrófono: si lo activas en pleno directo, no se oye hasta la siguiente transmisión.
- Mesa de Audio: los controles de Micrófono y Master Out no afectan al Motor de Streaming.
- Panel principal: muestra datos que no son reales, como la licencia, el consumo de tokens y la latencia. La tienda muestra compras sin efecto.

Sin corregir todavía:

- Subtítulos en vivo: no funcionan en la app de Windows.
- Red de Streamers: se puede leer, pero no publicar.

## Funciones

- Transmisión a varios destinos. Envía la misma señal por RTMP o RTMPS a Twitch, YouTube, Kick, Facebook, TikTok y otras plataformas, o a un servidor propio. Si un destino falla, los demás siguen en vivo.
- Host de IA. Lee los mensajes de Twitch y responde con OpenAI o Anthropic, usando tu propia clave. Puede decir las respuestas en voz alta y, si autorizas una cuenta, escribirlas en el chat. No lee los chats de YouTube, Facebook ni TikTok, y solo funciona mientras la app esté abierta.
- Subtítulos en vivo. Reconocen tu voz y la traducen a uno de 11 idiomas, pero solo en la versión web con Chrome, que no transmite a las plataformas.
- Filtros y lentes. Incluye 20 filtros de video, 8 lentes con seguimiento facial (MediaPipe), lentes propios creados a partir de una imagen y lentes de Snapchat mediante Camera Kit.
- Automatización 24/7. Reproduce en bucle listas de videos o música, o retransmite una emisora en vivo (Icecast, Shoutcast o HLS).
- Codificación por GPU. Usa NVENC, Quick Sync o AMF si están disponibles, y libx264 si no hay GPU compatible.
- Calidad automática. Elige la resolución según la CPU, la RAM y la GPU del equipo. La señal RTMP se limita a 1440p y 9 Mbps.

## Rendimiento

Medición del autor en un Intel Core i3-8130U de 2 núcleos con gráficos UHD 620, a 1080p30 y 6 Mbps contra una ingesta RTMP real:

| Codificador | Velocidad | CPU del codificador |
|---|---|---|
| libx264 (software) | 0.89x | 50.5 % |
| h264_qsv (GPU) | 1.00x | 15.6 % |

La prueba con GPU duró 11 minutos, sin fotogramas perdidos. Los resultados pueden variar en otros equipos.

## Instalación en Windows

1. Descarga `StreamAI-Studio-Windows-Setup.exe`.
2. Abre el instalador. Si aparece Windows SmartScreen, elige Más información y luego Ejecutar de todas formas. El aviso aparece porque el instalador no tiene firma digital.
3. Elige la carpeta de instalación y termina el asistente.

## Primeros pasos

Para transmitir:

1. Abre Motor de Streaming, elige la plataforma principal y pega su Stream Key. Puedes activar más destinos con sus propias claves.
2. Si la dirección predefinida de una plataforma no funciona, pega la URL del servidor que aparece en su panel. TikTok, Kick, Instagram, X, Rumble y Vimeo suelen asignar una propia.
3. Pulsa Iniciar Stream. Kick exige activar la verificación en dos pasos en tu cuenta.

Para usar el host de IA:

1. En Configuración, abre Motor IA (APIs), elige el proveedor, pega tu clave y guarda.
2. En Perfil de Usuario, vincula tu canal de Twitch o Kick.
3. Abre Director IA 24/7 y pulsa Iniciar Auto-Host para que diga las respuestas en voz alta y añada un mensaje de ánimo cada 4 minutos.

Con la clave y el canal configurados, la app genera una respuesta por cada mensaje del chat, aunque no hayas pulsado Iniciar Auto-Host. Cada respuesta consume saldo de tu proveedor de IA, según sus condiciones y precios.

Para que la IA escriba en el chat debes crear una aplicación de desarrollador en Twitch o Kick y autorizarla desde la app. Sin ese paso, las respuestas no se publican en el chat.

## Privacidad

Las claves se guardan en el equipo, cifradas con una clave derivada del dispositivo. Es una protección básica: evita la lectura casual, pero no resiste a un atacante con acceso al equipo. Estos datos salen del equipo:

- Los mensajes del chat y tu clave van al proveedor de IA que elijas.
- Las respuestas van a ElevenLabs, solo si configuras esa voz.
- Tu voz va al servicio de reconocimiento del navegador y el texto a Google Translate, solo si activas los subtítulos.
- Red de Streamers lee sus mensajes desde Firebase.
- La app consulta la API de GitHub al iniciar y cada 6 horas para buscar actualizaciones.
- Al vincular un canal de Twitch, la app lo verifica con el servicio decapi.me.

El micrófono de la transmisión está apagado por defecto. Solo se activa si lo enciendes y das permiso.

## Verificar las descargas

Las notas de cada [versión](https://github.com/santo29/streamai-downloads/releases) incluyen el SHA-256 de cada archivo. Para comprobarlo en PowerShell:

```powershell
Get-FileHash .\StreamAI-Studio-Windows-Setup.exe -Algorithm SHA256
```

También puedes analizar el archivo en [VirusTotal](https://www.virustotal.com) antes de instalarlo. Un programa sin firma digital puede dar algún falso positivo aislado.

## Uso responsable

Transmitir a varias plataformas a la vez, los canales automatizados 24/7 y usar música con copyright pueden chocar con los términos de Twitch, YouTube, TikTok y Kick, y con los derechos de autor. Algunas plataformas exigen un mínimo de seguidores para dar acceso a RTMP o desincentivan el contenido totalmente automático. Tú eres responsable de tus cuentas, así que revisa las reglas de cada plataforma.

## Términos

StreamAI Studio es freeware y se entrega sin garantía. Consulta [TERMS.md](TERMS.md).

## Soporte

Puedes informar de errores en [Issues](https://github.com/santo29/streamai-downloads/issues). Si el proyecto te resulta útil, puedes darle una estrella o hacer una [donación por PayPal](https://www.paypal.com/donate/?business=rodriguezsanto17%40gmail.com&no_recurring=0&currency_code=USD&item_name=Apoyo%20a%20StreamAI%20Studio).

Desarrollado por Santo Montilla ([santo29](https://github.com/santo29)) en República Dominicana.

<details>
<summary>English</summary>

StreamAI Studio is a free, closed-source Windows app for streaming to several platforms at once over RTMP. It includes an AI host for Twitch chat that uses your own OpenAI or Anthropic key. It also offers face filters, 24/7 playlists and GPU encoding. Version 1.8.2 has known problems, listed in Spanish above.

The web version and the Android APK let you try the studio, but they do not stream or answer chat with AI. See [TERMS.md](TERMS.md) for the terms of use, which are in Spanish.

</details>
