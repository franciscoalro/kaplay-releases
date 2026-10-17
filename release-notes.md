KA Play 4.10.91-PRE.

- Remove as mensagens de preparação e a espera artificial de 3 segundos antes do anúncio.
- Anúncio disponível abre diretamente; sem anúncio, o fluxo continua.
- Mantém limite entre anúncios, callbacks de continuação e proteção do ciclo de vida.
- Inclui os novos cartões de Continuar assistindo da 4.10.90 e a atualização do plugin FilmeFilms da branch de prévias.

Código: 2a949d6f2838311440ce600388a47b79d75eef9f.
Validação física do anúncio e do fluxo no aparelho permanece pendente.
Atualiza a prévia debug anterior com o mesmo pacote e certificado; a prévia de produção usa pacote próprio.

```kaplay-update
{
  "applicationId": "br.com.kaplay.app.prerelease.debug",
  "versionName": "4.10.91-PRE",
  "versionCode": 29870671,
  "sha256": "fcc972b47a3be3d02abddb25c7b2ee0630c3d5895bd0094c13a55b0fe276757a",
  "apkUrl": "https://github.com/franciscoalro/kaplay-releases/releases/download/pre-release/ka-play-4.10.91-PRE-debug.apk"
}
```
