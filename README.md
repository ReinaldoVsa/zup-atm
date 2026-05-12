# ATM ZUP - Sistema de Caixa Eletrônico Bluetooth

**v1.0.0 | Build 20260512**

PWA (Progressive Web App) para controle de ATM via Bluetooth, compatível com Web, Android e Desktop.

---

## 🚀 Deploy no GitHub Pages

### 1. Crie o repositório

```bash
git init
git add .
git commit -m "ATM ZUP v1.0.0"
git branch -M main
git remote add origin https://github.com/SEU_USER/atm-zup.git
git push -u origin main
```

### 2. Ative o GitHub Pages

1. Vá em **Settings → Pages**
2. Source: **Deploy from a branch**
3. Branch: **main** / folder: **/ (root)**
4. Clique **Save**

### 3. Acesse o app

```
https://SEU_USER.github.io/atm-zup/
```

---

## 📱 Instalar como App Android

1. Abra o link no **Chrome para Android**
2. Toque no menu (⋮) → **"Adicionar à tela inicial"**
3. O app abre em modo fullscreen como app nativo

---

## 🔵 Conexão Bluetooth

### Requisitos
- Chrome 85+ (Android/Desktop) ou Edge 85+
- Bluetooth ativo no dispositivo
- ATM ZUP com firmware Bluetooth (GATT server)

### UUIDs BLE (configurar em `js/app.js`)

| Constante | UUID padrão |
|-----------|-------------|
| `SERVICE_UUID` | `12345678-1234-1234-1234-123456789abc` |
| `CHAR_COMMAND_UUID` | `12345678-1234-1234-1234-123456789abd` |
| `CHAR_STATUS_UUID` | `12345678-1234-1234-1234-123456789abe` |
| `ATM_NAME_PREFIX` | `ATM-ZUP` |

Para conectar ao seu hardware real, atualize os UUIDs para corresponder ao firmware do ATM.

### Como conectar
1. Faça login como operador (aba **Perfil**)
2. Na aba **Operações**, toque em **SCAN BLUETOOTH**
3. Selecione o ATM na lista
4. A conexão é automática com reconexão ativada

---

## 🔐 Segurança

- **AES-256-GCM** — criptografia de comandos
- **HMAC-SHA256** — autenticação de mensagens
- **TLS 1.3** — transporte seguro
- **Zero Trust Policy** — verificação contínua
- **Device Fingerprint** — identificação do dispositivo

---

## 📁 Estrutura do Projeto

```
atm-zup/
├── index.html          # App principal (single page)
├── manifest.json       # PWA manifest
├── sw.js               # Service Worker (offline)
├── css/
│   └── style.css       # Estilos completos
├── js/
│   └── app.js          # Lógica completa do app
├── icons/
│   ├── icon-192.png    # Ícone PWA 192x192
│   └── icon-512.png    # Ícone PWA 512x512
└── README.md
```

---

## ⚙️ Customização do Hardware ATM

Para integrar com hardware real:

1. **Firmware do ATM**: implemente um GATT server Bluetooth com os UUIDs configurados
2. **Comando de saque**: o app envia JSON via característica BLE:
   ```json
   {
     "cmd": "RELEASE",
     "amount": 10000,
     "txId": "TX-ABC123",
     "timestamp": 1234567890,
     "operatorId": "Ana Rodrigues",
     "hmac": "A1B2C3D4"
   }
   ```
3. **Resposta do ATM**: notifique via característica de status

---

## 📋 Funcionalidades

- ✅ Scan BLE automático por ATMs próximos
- ✅ Conexão via UUID manual ou scan
- ✅ Login de operador com PIN
- ✅ Teclado numérico + valores rápidos
- ✅ Cálculo automático de notas
- ✅ Inventário de notas em tempo real
- ✅ Dashboard com histórico de transações
- ✅ Console operacional com logs
- ✅ Reconexão automática BLE
- ✅ Exportação de logs
- ✅ Instalável como PWA (Android/Desktop)
- ✅ Suporte offline via Service Worker
- ✅ Interface responsiva (mobile-first)

---

## 📄 Licença

Propriedade de ATM ZUP. Uso restrito a operadores autorizados.
