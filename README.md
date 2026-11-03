# StreamAI Studio

Transmite en vivo a varias plataformas a la vez desde Windows, con un host de IA para el chat de Twitch y Kick que usa tu propia clave.

[![Última versión](https://img.shields.io/github/v/release/santo29/streamai-downloads)](https://github.com/santo29/streamai-downloads/releases/latest)

StreamAI Studio es gratuito y de código cerrado. Este repositorio contiene los instaladores, las capturas, las notas de cada versión y la licencia. El código fuente no es público.

## Descargas

| Plataforma | Requisitos | Enlace |
|---|---|---|
| Windows | Windows 10 u 11 de 64 bits | [StreamAI-Studio-Windows-Setup.exe](https://github.com/santo29/streamai-downloads/releases/latest/download/StreamAI-Studio-Windows-Setup.exe) |
| Android | Android 7.0 o superior | [StreamAI-Studio-Android.apk](https://github.com/santo29/streamai-downloads/releases/latest/download/StreamAI-Studio-Android.apk) |
| Navegador | Chrome recomendado | [streamai-studio-db.web.app](https://streamai-studio-db.web.app) |

El instalador de Windows no tiene firma digital, así que Windows SmartScreen seguirá mostrando un aviso al instalarlo.

La versión completa es la de Windows, porque incluye el motor de transmisión local con FFmpeg. La versión web y el APK sirven para probar el estudio, pero no transmiten a las plataformas ni responden el chat con IA.

## Funciones

Capturas de la versión 1.9.0 con datos de ejemplo. Cada una dice qué hace esa función.

![Transmisión en vivo](docs/capturas/transmision-en-vivo.png)

![Varios destinos](docs/capturas/varios-destinos.png)

![Panel principal](docs/capturas/panel-principal.png)

![Host de IA](docs/capturas/host-de-ia.png)

![Configuración de IA](docs/capturas/configuracion-de-ia.png)

![Clips automáticos](docs/capturas/clips-automaticos.png)

![Filtros y lentes](docs/capturas/filtros-y-lentes.png)

![Plantillas](docs/capturas/plantillas.png)

![Mesa de Audio](docs/capturas/mesa-de-audio.png)

![Automatización de video](docs/capturas/automatizacion-video.png)

![Radio 24/7](docs/capturas/automatizacion-radio.png)

![Diagnóstico](docs/capturas/diagnostico.png)

## Instalación en Windows

1. Descarga StreamAI-Studio-Windows-Setup.exe.
2. Abre el instalador. Si aparece Windows SmartScreen, elige Más información y luego Ejecutar de todas formas. En Windows 11 con Smart App Control activado, Windows puede bloquear el instalador porque no está firmado.
3. Elige la carpeta de instalación y termina el asistente.

## Primeros pasos

Para transmitir:

1. Abre Motor de Streaming, elige la plataforma principal y pega su Stream Key. Puedes activar más destinos con sus propias claves.
2. Si la dirección predefinida de una plataforma no funciona, pega la URL del servidor que aparece en su panel. TikTok, Kick, Instagram, X, Rumble y Vimeo suelen asignar una propia.
3. Elige una fuente con Clonar Pantalla o en Fuentes A/V.
4. Activa el micrófono si quieres que se oiga tu voz. Viene apagado por defecto.
5. Pulsa Iniciar Stream. Kick exige activar la verificación en dos pasos en tu cuenta.

Para usar el host de IA:

1. En Configuración, abre Motor IA (APIs), elige el proveedor, pega tu clave y guarda.
2. En Perfil de Usuario, vincula tu canal de Twitch o Kick.
3. Abre Director IA 24/7 y pulsa Iniciar Auto-Host.

El host solo actúa con el Auto-Host encendido y hace como máximo una llamada a la IA cada 8 segundos. Cada respuesta consume saldo de tu proveedor de IA, según sus condiciones y precios. Para que la IA escriba en el chat de Twitch debes crear una aplicación de desarrollador en Twitch y autorizarla desde la app. En Kick la IA lee el chat y responde por voz. Sin ese paso, en Twitch las respuestas no se publican en el chat.

## Limitaciones conocidas

- Subtítulos en vivo: no funcionan en la app de Windows. En nuestra prueba con un micrófono simulado, el servicio de voz devuelve un error de red y no aparece texto. En la versión web con Chrome ese error no aparece, pero en nuestra prueba tampoco llegó texto, así que queda sin confirmar.
- Efectos de sonido: no entran en la transmisión si retransmites una emisora en vivo. Solo suenan en tus altavoces.
- En Kick, el host de IA responde por voz y no puede publicar en el chat.
- Red de Streamers: se puede leer, pero no publicar.
- APK de Android: sigue siendo el de la versión 1.6.0. No transmite ni responde el chat con IA.
- Voz del host de IA: suena en tus altavoces y no entra en la mezcla del directo. Solo pueden oírla tus espectadores si compartes pantalla con Clonar Pantalla, que captura el sonido del equipo.
- Chat de Kick: la app lo lee desde su página pública. Si Kick cambia su sistema, puede dejar de funcionar; en ese caso la app lo avisa.

## Estado de las pruebas

La versión 1.9.0 se probó en un Intel Core i3-8130U con Windows 10, usando un servidor RTMP local, cámara y micrófono simulados, un proveedor de IA simulado y los chats públicos de Twitch y Kick en solo lectura.

Sin probar todavía: transmitir a cuentas reales, claves reales de OpenAI, Anthropic, Google Gemini y ElevenLabs, publicar respuestas en el chat, una cámara y un micrófono físicos, los lentes faciales con un rostro real y Windows 11.

## Rendimiento

La app envía 3.5 Mbps a 720p y 6 Mbps a 1080p. Si tu subida no alcanza y el directo se retrasa, baja el bitrate sola y reconecta. Con un servidor local limitado a 6 Mbps de subida a 1080p, en 90 segundos de directo llegan 88.7 segundos de video. Tu internet y los servidores de cada plataforma pueden cambiar este resultado.

Medición del autor en un Intel Core i3-8130U de 2 núcleos con gráficos UHD 620, a 1080p30 y 6 Mbps contra una ingesta RTMP real:

| Codificador | Velocidad | CPU del codificador |
|---|---|---|
| libx264 (software) | 0.89x | 50.5 % |
| h264_qsv (GPU) | 1.00x | 15.6 % |

La prueba con GPU duró 11 minutos, sin fotogramas perdidos. La señal RTMP se limita a 1440p y 9 Mbps. En reposo, en el Motor de Streaming, la versión 1.9.0 usa entre 8 % y 10 % de la CPU en ese mismo equipo. Los resultados pueden variar en otros equipos.

## Privacidad

Las claves se guardan en el equipo, cifradas con una clave derivada del dispositivo. Es una protección básica: evita la lectura casual, pero no resiste a un atacante con acceso al equipo. Estos datos salen del equipo:

- Con el Auto-Host encendido, los mensajes del chat y tu clave van al proveedor de IA que elijas.
- Las respuestas van a ElevenLabs, solo si configuras esa voz.
- Si activas los subtítulos, tu voz va al servicio de reconocimiento del navegador y el texto a Google Translate.
- Red de Streamers lee sus mensajes desde Firebase.
- La app consulta la API de GitHub al iniciar y cada 6 horas para buscar actualizaciones.
- Al vincular un canal de Twitch, la app lo verifica con el servicio decapi.me.

El micrófono está apagado por defecto y la cámara no lo abre. Solo se activa si lo enciendes y das permiso.

## Verificar las descargas

Las notas de cada [versión](https://github.com/santo29/streamai-downloads/releases) incluyen el SHA-256 de cada archivo. Para comprobarlo en PowerShell:

```powershell
Get-FileHash .\StreamAI-Studio-Windows-Setup.exe -Algorithm SHA256
```

También puedes analizar el archivo en [VirusTotal](https://www.virustotal.com) antes de instalarlo. Un programa sin firma digital puede dar algún falso positivo aislado.

## Uso responsable

Transmitir a varias plataformas a la vez, los canales automatizados 24/7 y usar música con copyright pueden chocar con los términos de Twitch, YouTube, TikTok y Kick, y con los derechos de autor. Algunas plataformas exigen un mínimo de seguidores para dar acceso a RTMP o desincentivan el contenido totalmente automático. Tú eres responsable de tus cuentas, así que revisa las reglas de cada plataforma.

## Licencia

StreamAI Studio es freeware y se entrega sin garantía. Consulta [LICENSE](LICENSE) y [TERMS.md](TERMS.md). Los componentes de terceros conservan sus licencias, listadas en [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

Los nombres de las plataformas solo indican adónde puede transmitir la app. StreamAI Studio no tiene acuerdo ni patrocinio con ellas.

## Soporte

Puedes informar de errores en [Issues](https://github.com/santo29/streamai-downloads/issues). Si el proyecto te resulta útil, puedes darle una estrella o hacer una [donación por PayPal](https://www.paypal.com/donate/?business=rodriguezsanto17%40gmail.com&no_recurring=0&currency_code=USD&item_name=Apoyo%20a%20StreamAI%20Studio).

Desarrollado por Santo Montilla ([santo29](https://github.com/santo29)) en República Dominicana.

<details>
<summary>English</summary>

StreamAI Studio is a free, closed-source Windows app for streaming to several platforms at once over RTMP. It includes an AI host for Twitch and Kick chat that uses your own OpenAI, Anthropic or Google Gemini key. It also offers automatic clips, video filters and face lenses, overlays, an audio mixer, 24/7 playlists and radio, and GPU encoding.

Live captions do not work in the Windows app. The web version and the Android APK let you try the studio, but they do not stream or answer chat with AI. The installer is not digitally signed, so Windows SmartScreen will show a warning. See [LICENSE](LICENSE) for the terms of use, which are in Spanish. Platform names only show where the app can stream. StreamAI Studio has no agreement with or sponsorship from those platforms.

</details>
