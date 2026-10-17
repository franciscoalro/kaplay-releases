KA Play 4.10.97-PRE — primeira etapa de Detalhes

- Cabeçalho integrado à capa no celular, com fundo semitransparente e opacidade ao rolar.
- Degradês suaves e paleta preto azulado, textos claros e destaque violeta.
- Carregamento, erro, capa ausente e trailer reservam espaço para os controles com fundo opaco.
- Preserva fontes, capa de 280dp, ordem da sinopse e cards uniformes aprovados.
- Mantém as ações existentes; reorganização de botões/lista fica para a segunda etapa do plano.

Builds prévia/estável debug, 133 testes por variante e lint sem erros aprovados. Fonte f3b97cdf0677688a1bc99ba4cbf13dda9aed3eda. Aparência, painéis, trailer/tela cheia, foco e insets no Redmi ainda precisam de homologação.

APK de teste br.com.kaplay.app.prerelease.debug: atualiza a prévia debug 4.10.96 com a mesma assinatura. Instala separado da produção; não substitui diretamente a produção 4.10.92 de outro certificado.

```kaplay-update
{
  "applicationId": "br.com.kaplay.app.prerelease.debug",
  "versionName": "4.10.97-PRE",
  "versionCode": 29871300,
  "sha256": "060b3bb7756b4ffc226dbc0416cd34721bacf5d279d63b4c9180fa2e60d7c9c7",
  "apkUrl": "https://github.com/franciscoalro/kaplay-releases/releases/download/pre-release/ka-play-4.10.97-PRE-debug.apk"
}
```
