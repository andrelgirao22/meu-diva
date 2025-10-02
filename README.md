# Meu Diva - Backend API

Backend para aplicativo mobile de suporte terapêutico com recursos de autoconhecimento e gestão emocional.

## 🎯 Sobre o Projeto

API REST para app de psicanálise focado em:
- Diário emocional com anexos
- Caixinha das emoções (conteúdo positivo)
- Recursos de emergência emocional
- Sistema de assinaturas (freemium)
- Gestão de perfil e contatos de emergência

## 🛠️ Stack Tecnológica

- **Spring Boot 3.x** + Java 17+
- **PostgreSQL 15** com Spring Data JPA
- **Spring Security** + JWT para autenticação
- **AWS S3** para armazenamento de arquivos
- **Stripe/PagSeguro** para pagamentos
- **SpringDoc OpenAPI** para documentação

## 📂 Estrutura Principal

```
src/main/java/com/psique/
├── controller/     # REST endpoints
├── service/        # Lógica de negócio
├── repository/     # Acesso a dados
├── model/          # Entidades JPA
├── dto/            # Request/Response objects
├── config/         # Configurações (Security, JWT)
└── exception/      # Tratamento de erros
```

## 🔌 APIs Principais

- `/api/auth/*` - Autenticação e registro
- `/api/users/*` - Perfil do usuário
- `/api/diary/*` - Entradas do diário
- `/api/emotion-box/*` - Caixinha das emoções
- `/api/emotions/*` - Registro de emoções
- `/api/emergency/*` - Recursos e contatos de emergência
- `/api/subscriptions/*` - Planos e pagamentos

## 🗄️ Banco de Dados

Principais entidades:
- **Users** - Usuários do sistema
- **Diary Entries** - Entradas do diário emocional
- **Emotions** - Registro de emoções e intensidade
- **Emotion Box Items** - Conteúdo positivo personalizado
- **Emergency Resources/Contacts** - Recursos de crise
- **Subscriptions** - Planos de assinatura

## 🚀 Como Executar

```bash
# Executar localmente
./mvnw spring-boot:run

# Build
./mvnw clean package

# Testes
./mvnw test
```

## 🔒 Segurança

- JWT com refresh tokens
- Criptografia end-to-end para dados sensíveis
- HTTPS obrigatório
- Rate limiting
- Compliance LGPD

## 📊 Modelo de Negócio

**Plano Gratuito:**
- Diário limitado (10 entradas/mês)
- Caixinha com 5 itens
- Recursos básicos de emergência

**Plano Premium:**
- Diário e caixinha ilimitados
- Estatísticas avançadas
- Export de dados
- Backup automático

## 🛣️ Roadmap

- **Fase 1**: MVP com funcionalidades core
- **Fase 2**: Sistema de assinaturas
- **Fase 3**: Analytics e melhorias UX
- **Fase 4**: Integração com profissionais

---

**Criado por:** Andreia Lima Girão
**Versão:** 1.0.0
**Data:** Outubro 2025