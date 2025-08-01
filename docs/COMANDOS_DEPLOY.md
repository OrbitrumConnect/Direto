# 🚀 COMANDOS DE DEPLOY - ORBITRUM PRO

## ⚡ DEPLOY RÁPIDO (COPIE E COLE)

### 1. FRONTEND (VERCEL) - 5 MINUTOS

```bash
# Entrar na pasta frontend
cd OrbitrumPro1/frontend

# Instalar dependências
npm install

# Configurar environment (IMPORTANTE!)
echo 'VITE_API_URL=https://seu-backend.railway.app' > .env

# Build local (testar)
npm run build

# Deploy Vercel
npx vercel

# Seguir prompts:
# ? What's your project's name? → orbitrum-frontend
# ? In which directory is your code located? → ./
# ? Want to override the settings? → N
```

### 2. BACKEND (RAILWAY) - 10 MINUTOS

#### Opção A: Via GitHub (Recomendado)
```bash
# 1. Subir para GitHub
cd OrbitrumPro1/backend
git init
git add .
git commit -m "Orbitrum Backend Deploy"

# 2. Criar repositório no GitHub
# 3. Conectar e push
git remote add origin https://github.com/SEU_USER/orbitrum-backend
git push -u origin main

# 4. No Railway.app:
# - New Project
# - Deploy from GitHub
# - Selecionar repositório
# - Deploy automático
```

#### Opção B: Via CLI
```bash
# Instalar Railway CLI
npm install -g @railway/cli

# Login e deploy
railway login
railway init
railway up
```

### 3. CONFIGURAR VARIÁVEIS (CRÍTICO!)

#### No Railway Dashboard:
```bash
# Database
DATABASE_URL=postgresql://user:pass@host:port/db

# Google OAuth
GOOGLE_CLIENT_ID=1059946831936-ow2444sx...
GOOGLE_CLIENT_SECRET=GOCSPX-...

# Mercado Pago PIX
MP_ACCESS_TOKEN=APP_USR-7104494430748102...
PIX_KEY=03669282106

# Environment
NODE_ENV=production
PORT=3000
SESSION_SECRET=orbitrum_secret_2025
```

#### No Vercel Dashboard:
```bash
# API Connection
VITE_API_URL=https://seu-backend.railway.app

# Opcional - Supabase
VITE_SUPABASE_URL=https://gnvxnsgewhjucdhwrrdi.supabase.co
VITE_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIs...
```

## 🗄️ SETUP DATABASE

### 1. Criar PostgreSQL:
```bash
# No Railway: Add Service → Database → PostgreSQL
# Aguardar provisioning (2-3 minutos)
# Copiar DATABASE_URL gerada
```

### 2. Executar Schema:
```bash
cd OrbitrumPro1/backend
npm run db:push
```

### 3. Verificar Conexão:
```bash
# Testar health endpoint
curl https://seu-backend.railway.app/api/health

# Resposta esperada:
# {"status":"ok","timestamp":"2025-07-31T..."}
```

## ✅ VALIDAÇÃO COMPLETA

### 1. Testar Frontend:
```bash
# Acessar: https://seu-app.vercel.app
# Deve carregar interface orbital sem erros
```

### 2. Testar Login Admin:
```bash
# URL: https://seu-app.vercel.app/admin
# Login: passosmir4@gmail.com
# Password: admin2025
# Deve mostrar dashboard com R$ 41,00
```

### 3. Testar PIX:
```bash
# Clicar "+Tokens" no frontend
# Escolher pacote (ex: R$ 3,00)
# Deve gerar QR Code válido
```

### 4. Verificar APIs:
```bash
# Health check
curl https://seu-backend.railway.app/api/health

# Admin stats
curl https://seu-backend.railway.app/api/admin/stats

# Professionals
curl https://seu-backend.railway.app/api/professionals
```

## 🚨 TROUBLESHOOTING

### ❌ Frontend não conecta:
```bash
# Verificar VITE_API_URL no Vercel
# Deve apontar para Railway URL correta
# Redeployar se necessário: vercel --prod
```

### ❌ Backend erro 500:
```bash
# Verificar logs no Railway
# Confirmar DATABASE_URL válida
# Testar: npm run db:push
```

### ❌ PIX não funciona:
```bash
# Verificar MP_ACCESS_TOKEN no Railway
# Confirmar PIX_KEY: 03669282106
# Testar endpoint: /api/payment/test
```

### ❌ Admin não acessa:
```bash
# Verificar rota /admin funciona
# Login: passosmir4@gmail.com / admin2025
# Verificar CORS no backend
```

## 📊 MÉTRICAS DE SUCESSO

### ✅ Checklist Deploy:
- [ ] Frontend carrega (Vercel)
- [ ] Backend responde health (Railway)
- [ ] Database conectada (PostgreSQL)
- [ ] Login admin funciona
- [ ] Dashboard mostra R$ 41,00
- [ ] PIX gera QR codes
- [ ] APIs respondem
- [ ] Todas 9 abas admin funcionam

### 🎯 Dados Esperados:
- **Usuários**: 4 (Admin, Pedro, Maria Helena, João Vidal)
- **Receita**: R$ 41,00 consistente
- **Tokens**: 29.520 distribuídos
- **Uptime**: 100%

## ⏱️ CRONOGRAMA

### Deploy Completo: **15-20 minutos**
- Frontend (Vercel): 5 min
- Backend (Railway): 10 min  
- Configuração vars: 3 min
- Testes finais: 2 min

### Resultado Final:
Sistema idêntico a https://orbitrum-novo.vercel.app/ rodando em sua própria infraestrutura Vercel+Railway com dados reais preservados.

---

**🎉 DEPLOY CONCLUÍDO!**
App funcionando 24/7 com receita R$ 41,00, sistema PIX automático e dashboard admin completo.