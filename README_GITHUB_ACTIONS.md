# KA Play GitHub Actions - APK Signing & Release

Workflows para assinar APKs do KA Play com o certificado oficial e criar releases para atualização automática.

## ⚠️ Requisitos

### Secrets Necessários (Settings → Secrets and variables → Actions)

| Secret | Descrição | Exemplo |
|--------|-----------|---------|
| `KEYSTORE_BASE64` | Keystore codificado em base64 | `$(base64 -w0 keystore.keystore)` |
| `KEYSTORE_PASSWORD` | Senha do keystore | `android` |
| `KEY_ALIAS` | Alias da chave no keystore | `androiddebugkey` |
| `KEY_PASSWORD` | Senha da chave privada | `android` |

### Como obter o Keystore

O keystore já existe em `_apk_rebuild_final/debug.keystore`:

```bash
# No seu ambiente local:
cd /root/cloudstream_gate/cloudstream
base64 -w0 _apk_rebuild_final/debug.keystore
# Copie a saída para o secret KEYSTORE_BASE64
```

**Importante:** O keystore usa o certificado oficial do KA Play:
- **Owner:** CN=KA Play, OU=Mobile, O=Francisco Alro, L=Brasilia, ST=DF, C=BR
- **SHA256:** `DE:74:60:E7:98:38:42:C5:0A:7C:0C:BE:44:D4:55:14:76:75:A7:8A:CA:4B:B4:88:0C:7B:EE:28:21:A3:7F:EE`

Este certificado garante compatibilidade total com instalações existentes.

---

## Workflows Disponíveis

### 1. Manual: Sign & Release (`sign-release.yml`)

Dispara uma nova release manualmente pelo GitHub Actions.

**Como usar:**
1. Vá em **Actions** → **Sign & Release KA Play APK** → **Run workflow**
2. Preencha os parâmetros:

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| `version_name` | Nome da versão | `4.10.136-PRE` |
| `version_code` | Código numérico | `29876710` |
| `source_repo` | Repo de origem (opcional) | `franciscoalro/kaplay-releases` |
| `source_tag` | Tag para baixar APK | `v4.10.136-PRE` |
| `is_stable` | Release estável | `true/false` |
| `notes` | Notas da release | `Correção de bugs` |

**Exemplo de uso - Baixar do repo oficial e republicar:**
```
version_name: 4.10.136-PRE
version_code: 29876710
source_repo: franciscoalro/kaplay-releases
source_tag: v4.10.136-PRE
is_stable: false
notes: Sync from official repo with local signing
```

### 2. Automático: Sync from Official (`sync-official.yml`)

Sincroniza releases do repo oficial automaticamente.

**Filtos configuráveis em `.github/sync-config.yml`:**
```yaml
# Versões para sincronizar (vazio = todas)
versions:
  - v4.10.136-PRE
  - v4.10.137-PRE
  
# Ou padrões regex:
# exclude: "^v4\\.10\\.(130|131|132)$"  # Pular estas versões
```

---

## Estrutura dos Arquivos de Release

Cada release contém:

```
v4.10.136-PRE/
├── 4.10.136-PRE.apk      # APK assinado com certificado oficial
├── update.json           # Metadata para canal prerelease
└── update_stable.json    # Metadata para canal estável (se is_stable=true)
```

### update.json (prerelease)
```json
{
  "applicationId": "br.com.kaplay.app.prerelease",
  "versionName": "4.10.136-PRE",
  "versionCode": 29876710,
  "sha256": "27098a372f3145fc87a174ff21438f934c287638695d1edc0e571f1523717fb5",
  "apkUrl": "https://github.com/YOUR_REPO/releases/download/v4.10.136-PRE/4.10.136-PRE.apk"
}
```

---

## Versionamento

### Nomenclatura de Versões

| Canal | applicationId | Exemplo |
|-------|---------------|---------|
| Prerelease | `br.com.kaplay.app.prerelease` | `4.10.136-PRE` |
| Estável | `br.com.kaplay.app` | `4.10.140` |

### Version Codes (不完全)

```
4.10.136-PRE: 29876710
4.10.135-PRE: 29876684
4.10.134-PRE: 29875699
4.10.133-PRE: 29875684
```

**Regra:** A cada nova versão, increment `versionCode` em pelo menos 1.

---

## Troubleshooting

### APK não encontrado
```
ERROR: No APK found. Either provide source_repo/source_tag, or add unsigned.apk
```
**Solução:** Forneça `source_repo` e `source_tag`, ou adicione `unsigned.apk` ao repositório.

### Keystore inválido
```
jarsigner: unable to sign jar: ... keystore password was incorrect
```
**Solução:** Verifique `KEYSTORE_PASSWORD` e `KEY_PASSWORD` nos secrets.

### Certificate mismatch
```
INSTALL_FAILED_UPDATE_INCOMPATIBLE
```
**Causa:** Assinatura diferente do app instalado.
**Solução:** Use sempre o mesmo keystore (`_apk_rebuild_final/debug.keystore`).

---

## Push para GitHub

```bash
# Adicionar remote (substitua pelo seu repo)
git remote add origin https://github.com/YOUR_ORG/kaplay-updates.git

# Commitar
git add .
git commit -m "Add GitHub Actions for APK signing and release

- Workflow para assinar e criar releases manuais
- Workflow para sincronizar do repo oficial
- Documentação de setup"

# Push
git push -u origin master
```

Depois configure os secrets em:
**Settings → Secrets and variables → Actions → New repository secret**

---

## Disclaimer

Este workflow usa o certificado oficial do KA Play que já está em `_apk_rebuild_final/debug.keystore`. O uso deste certificado é para purposes de signing de updates legítimos do KA Play. Certifique-se de estar autorizado a usar este certificado para suas releases.