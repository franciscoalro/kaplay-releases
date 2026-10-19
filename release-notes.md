KA Play 4.10.111-PRE

- Redesign das telas de boas-vindas, entrada, cadastro e recuperação: campos contrastantes, textos moderados, rolagem e botões consistentes.
- Seleção de perfis mais compacta no celular, com Novo perfil e indicação do perfil atual.
- Conta e backup com fechamento direto, cópias separadas do estado de login e ações de salvar/restaurar em largura completa.
- Corrige a associação do horário da cópia à conta e protege a sessão durante exportação/restauração de backups.
- Sincronização automática de dados de acompanhamento no Supabase: envio após alterações, recuperação em aparelho vazio, nova tentativa com rede e proteção de alterações simultâneas.
- Requer tabela user_backups versionada e RLS do projeto configurado; conflitos preservam as cópias até escolha explícita.
- Mantém autenticação atual por e-mail, fluxos existentes e refinamentos de Home, Detalhes e Geral.

Builds prévia/estável debug, testes de regressão e lint verificados antes da publicação. Validação no aparelho permanece pendente.

APK de teste, pacote separado, assinatura compatível com o canal debug anterior. Fonte 9822f52f4cbadcfb0a07526633e89e894d271518.

```kaplay-update
{
  "applicationId": "br.com.kaplay.app.prerelease.debug",
  "versionName": "4.10.111-PRE",
  "versionCode": 29874031,
  "sha256": "3f34e13e18667f2964bb7365ae3a99abc975e6d300e799be77879cb8696c4dde",
  "apkUrl": "https://github.com/franciscoalro/kaplay-releases/releases/download/pre-release/ka-play-4.10.111-PRE-debug.apk"
}
```
