<!-- Plantilla para las notas de cada versión.
     La app muestra las tres primeras líneas en el aviso de actualización, hasta
     180 caracteres. Escríbelas como frases cortas en texto plano, sin títulos.
     Antes de publicar, rellena los enlaces de VirusTotal y los SHA-256. -->
Primer cambio importante, en una frase corta.
Segundo cambio importante.
Tercer cambio importante.

## Cambios

- Un cambio por línea, en lenguaje concreto. Incluye la cifra si hay una medición.

## Descargas

- Windows: `StreamAI-Studio-Windows-Setup.exe`
- Android: `StreamAI-Studio-Android.apk`
- Versión web, sin instalar: https://streamai-studio-db.web.app

El instalador de Windows no tiene firma digital. Si aparece SmartScreen, elige Más información y luego Ejecutar de todas formas.

## Verificación

VirusTotal:

- Windows: <!-- enlace del informe -->
- Android: <!-- enlace del informe -->

SHA-256:

- `StreamAI-Studio-Windows-Setup.exe`: `<hash>`
- `StreamAI-Studio-Android.apk`: `<hash>`

Para comprobarlo en PowerShell: `Get-FileHash <archivo> -Algorithm SHA256`
