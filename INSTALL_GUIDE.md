# 📖 GUIA DE INSTALAÇÃO ORBITRUM PRO

## 🎯 OBJETIVO
Implementar o sistema Orbitrum Connect Pro com arquitetura híbrida:
- **Frontend**: Vercel (React + TypeScript)
- **Backend**: Railway (Node.js + Express + PostgreSQL)

## ⚡ INSTALAÇÃO RÁPIDA (15 MINUTOS)

### 1. FRONTEND (VERCEL)

```bash
# 1. Entrar na pasta frontend
cd OrbitrumPro1/frontend

# 2. Instalar dependências
npm install

# 3. Configurar variáveis (criar .env)
echo 'VITE_API_URL=https://seu-backend.railway.app' > .env

# 4. Build local (testar)
npm run build

# 5. Deploy Vercel
npx vercel
# Seguir prompts: Yes → Nome do projeto → Deploy
```

### 2. BACKEND (RAILWAY)

#### Opção A: Via GitHub (Recomendado)
```bash
# 1. Subir código para GitHub
cd OrbitrumPro1/backend
git init
git add .
git commit -m "Orbitrum Backend"
git remote add origin https://github.com/SEU_USER/orbitrum-backend
git push -u origin main

# 2. No Railway.app:
# - Conectar GitHub
# - Selecionar repositório
# - Deploy automático
```

#### Opção B: Via CLI
```bash
# 1. Instalar Railway CLI
npm install -g @railway/cli

# 2. Login e deploy
railway login
railway init
railway up
```

### 3. CONFIGURAR VARIÁVEIS

#### No Railway (Backend):
```bash
DATABASE_URL=postgresql://user:pass@host:port/db
GOOGLE_CLIENT_ID=1059946831936-ow2444sx...
GOOGLE_CLIENT_SECRET=GOCSPX-...
MP_ACCESS_TOKEN=APP_USR-7104494430748102...
PIX_KEY=03669282106
NODE_ENV=production
PORT=3000
```

#### No Vercel (Frontend):
```bash
VITE_API_URL=https://seu-backend.railway.app
```

## 🗄️ CONFIGURAR DATABASE

### 1. Criar PostgreSQL no Railway:
```bash
# No painel Railway:
# Add Service → Database → PostgreSQL
# Copiar DATABASE_URL gerada
```

### 2. Executar migrações:
```bash
cd backend
npm run db:push
npm run db:seed  # Dados iniciais
```

## ✅ TESTAR FUNCIONAMENTO

### 1. Verificar Backend:
```bash
curl https://seu-backend.railway.app/api/health
# Resposta: {"status":"ok","timestamp":"..."}
```

### 2. Verificar Frontend:
```bash
# Acessar: https://seu-app.vercel.app
# Login: passosmir4@gmail.com / admin2025
# Dashboard admin deve carregar com R$ 41,00
```

### 3. Testar PIX:
```bash
# No frontend: Clicar "+Tokens" 
# Deve gerar QR Code válido
# Webhook deve creditar automaticamente
```

## 🚨 PROBLEMAS COMUNS

### Frontend não conecta backend:
```bash
# Verificar VITE_API_URL no Vercel
# Deve apontar para Railway URL
```

### Backend erro 500:
```bash
# Verificar DATABASE_URL no Railway
# Testar conexão: npm run db:test
```

### PIX não funciona:
```bash
# Verificar MP_ACCESS_TOKEN no Railway
# Testar endpoint: /api/payment/test
```

## 📊 VALIDAÇÃO FINAL

### ✅ Checklist Funcionamento:
- [ ] Frontend carrega sem erros
- [ ] Login admin funciona
- [ ] Dashboard mostra R$ 41,00
- [ ] Sistema PIX gera QR codes
- [ ] Backend responde /api/health
- [ ] Database conectada
- [ ] Todas as 9 abas admin funcionam

### 🎯 Métricas Esperadas:
- **Usuários**: 4 (Admin, Pedro, Maria Helena, João Vidal)
- **Receita**: R$ 41,00 
- **Tokens**: 29.520 distribuídos
- **Conversão**: 100%

## 🔧 COMANDOS ÚTEIS

### Frontend:
```bash
npm run dev          # Desenvolvimento local
npm run build        # Build produção
npm run preview      # Preview build
```

### Backend:
```bash
npm run dev          # Desenvolvimento local  
npm run build        # Build produção
npm run start        # Iniciar produção
npm run db:push      # Aplicar schema
npm run db:studio    # Interface visual DB
```

## 📞 SUPORTE

Em caso de problemas:
1. Verificar logs no Railway/Vercel
2. Testar endpoints individualmente
3. Validar variáveis de ambiente
4. Confirmar database conectado

**Tempo estimado total**: 15-30 minutos
**Resultado**: Sistema idêntico a https://orbitrum-novo.vercel.app/