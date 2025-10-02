# Projeto App de Psicanálise

## 📱 Sugestões de Nomes

### Opção 1: **MenteSerena**
*Transmite paz e equilíbrio emocional*

### Opção 2: **AcolheMente**
*Combina acolhimento com saúde mental*

### Opção 3: **InnerSpace**
*Espaço interior, moderno e internacional*

### Opção 4: **Refúgio Emocional**
*Direto e acolhedor*

### Opção 5: **Psique+**
*Simples, profissional e sugere evolução*

### Opção 6: **Lima Terapia Digital**
*Personalizado com o sobrenome da criadora*

---

## 🎯 Visão Geral do Projeto

Aplicativo mobile para suporte terapêutico com recursos de autoconhecimento e gestão emocional, destinado a pacientes em processo terapêutico ou que buscam ferramentas de apoio psicológico.

### Diferenciais
- Foco em psicanálise e autoconhecimento
- Recursos para gestão de crises emocionais
- Integração com profissionais (futura expansão)
- Modelo de negócio por assinatura

---

## 🏗️ Arquitetura do Sistema

```
┌─────────────────┐
│  Flutter App    │
│   (Android/iOS) │
└────────┬────────┘
         │ HTTPS/REST
         ▼
┌─────────────────┐
│   API Gateway   │
│   (Load Bal.)   │
└────────┬────────┘
         │
         ▼
┌─────────────────────────────────┐
│      Backend (Spring Boot)      │
│  ┌──────────┬────────────────┐  │
│  │ Auth     │ Subscription   │  │
│  │ Service  │ Service        │  │
│  ├──────────┼────────────────┤  │
│  │ Diary    │ Emotions       │  │
│  │ Service  │ Service        │  │
│  ├──────────┼────────────────┤  │
│  │Emergency │ Analytics      │  │
│  │ Service  │ Service        │  │
│  └──────────┴────────────────┘  │
└────────┬────────────────────────┘
         │
    ┌────┴────┐
    ▼         ▼
┌────────┐ ┌──────────┐
│PostGres│ │ S3/Cloud │
│   DB   │ │ Storage  │
└────────┘ └──────────┘
```

---

## 📂 Estrutura de Pastas

### Backend (Spring Boot)

```
psique-backend/
├── src/main/java/com/psique/
│   ├── config/
│   │   ├── SecurityConfig.java
│   │   ├── JwtConfig.java
│   │   └── CloudStorageConfig.java
│   ├── controller/
│   │   ├── AuthController.java
│   │   ├── UserController.java
│   │   ├── DiaryController.java
│   │   ├── EmotionBoxController.java
│   │   ├── EmergencyController.java
│   │   └── SubscriptionController.java
│   ├── service/
│   │   ├── AuthService.java
│   │   ├── UserService.java
│   │   ├── DiaryService.java
│   │   ├── EmotionBoxService.java
│   │   ├── EmergencyService.java
│   │   ├── SubscriptionService.java
│   │   └── CloudStorageService.java
│   ├── repository/
│   │   ├── UserRepository.java
│   │   ├── DiaryEntryRepository.java
│   │   ├── EmotionRepository.java
│   │   ├── EmergencyContactRepository.java
│   │   └── SubscriptionRepository.java
│   ├── model/
│   │   ├── User.java
│   │   ├── DiaryEntry.java
│   │   ├── Emotion.java
│   │   ├── EmotionBox.java
│   │   ├── EmergencyContact.java
│   │   ├── EmergencyResource.java
│   │   └── Subscription.java
│   ├── dto/
│   │   ├── request/
│   │   └── response/
│   ├── exception/
│   │   ├── GlobalExceptionHandler.java
│   │   └── CustomExceptions.java
│   └── util/
│       ├── JwtUtil.java
│       └── DateUtil.java
├── src/main/resources/
│   ├── application.yml
│   ├── application-dev.yml
│   └── application-prod.yml
└── pom.xml
```

### Frontend (Flutter)

```
psique-app/
├── lib/
│   ├── main.dart
│   ├── app/
│   │   ├── routes/
│   │   └── themes/
│   ├── core/
│   │   ├── constants/
│   │   ├── utils/
│   │   └── services/
│   │       ├── api_service.dart
│   │       ├── auth_service.dart
│   │       ├── storage_service.dart
│   │       └── subscription_service.dart
│   ├── features/
│   │   ├── auth/
│   │   │   ├── models/
│   │   │   ├── controllers/
│   │   │   └── views/
│   │   ├── diary/
│   │   │   ├── models/
│   │   │   ├── controllers/
│   │   │   └── views/
│   │   ├── emotion_box/
│   │   │   ├── models/
│   │   │   ├── controllers/
│   │   │   └── views/
│   │   ├── emergency/
│   │   │   ├── models/
│   │   │   ├── controllers/
│   │   │   └── views/
│   │   ├── profile/
│   │   └── subscription/
│   └── shared/
│       ├── widgets/
│       └── models/
├── assets/
│   ├── images/
│   ├── icons/
│   └── animations/
├── pubspec.yaml
└── README.md
```

---

## 🛠️ Stack Tecnológica

### Backend
- **Framework**: Spring Boot 3.x
- **Linguagem**: Java 17+
- **Banco de Dados**: PostgreSQL 15
- **ORM**: Spring Data JPA / Hibernate
- **Autenticação**: Spring Security + JWT
- **Pagamentos**: Stripe/PagSeguro SDK
- **Cloud Storage**: AWS S3 ou Google Cloud Storage
- **Cache**: Redis (opcional)
- **Documentação**: SpringDoc OpenAPI (Swagger)

### Frontend
- **Framework**: Flutter 3.x
- **Linguagem**: Dart 3.x
- **State Management**: Provider / Riverpod
- **HTTP Client**: Dio
- **Local Storage**: Hive / SQLite
- **Autenticação**: flutter_secure_storage
- **UI**: Material Design 3

### DevOps
- **CI/CD**: GitHub Actions / GitLab CI
- **Containerização**: Docker
- **Orquestração**: Kubernetes (opcional)
- **Cloud**: AWS / Google Cloud / Azure

---

## 💾 Modelo de Dados

### Users
```sql
CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    name VARCHAR(255) NOT NULL,
    phone VARCHAR(20),
    birth_date DATE,
    profile_picture_url TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    last_login TIMESTAMP,
    is_active BOOLEAN DEFAULT true
);
```

### Subscriptions
```sql
CREATE TABLE subscriptions (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID REFERENCES users(id),
    plan_type VARCHAR(50) NOT NULL, -- FREE, MONTHLY, YEARLY
    status VARCHAR(50) NOT NULL, -- ACTIVE, CANCELLED, EXPIRED
    start_date TIMESTAMP NOT NULL,
    end_date TIMESTAMP,
    payment_gateway VARCHAR(50),
    payment_id VARCHAR(255),
    amount DECIMAL(10,2),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Diary Entries
```sql
CREATE TABLE diary_entries (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID REFERENCES users(id),
    title VARCHAR(255),
    content TEXT NOT NULL,
    mood_rating INTEGER CHECK (mood_rating BETWEEN 1 AND 10),
    tags TEXT[], -- array de tags
    attachments JSONB, -- URLs de fotos/áudios
    is_private BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Emotions
```sql
CREATE TABLE emotions (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID REFERENCES users(id),
    emotion_type VARCHAR(100) NOT NULL, -- JOY, SADNESS, ANGER, etc
    intensity INTEGER CHECK (intensity BETWEEN 1 AND 10),
    trigger TEXT,
    notes TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Emotion Box
```sql
CREATE TABLE emotion_box_items (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID REFERENCES users(id),
    type VARCHAR(50) NOT NULL, -- QUOTE, IMAGE, AUDIO, VIDEO
    title VARCHAR(255),
    content TEXT,
    file_url TEXT,
    category VARCHAR(100), -- CALM, MOTIVATION, REFLECTION
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Emergency Resources
```sql
CREATE TABLE emergency_resources (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    title VARCHAR(255) NOT NULL,
    description TEXT,
    type VARCHAR(50) NOT NULL, -- HOTLINE, TECHNIQUE, ARTICLE
    content TEXT,
    phone_number VARCHAR(20),
    url TEXT,
    priority INTEGER DEFAULT 0,
    is_active BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Emergency Contacts
```sql
CREATE TABLE emergency_contacts (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID REFERENCES users(id),
    name VARCHAR(255) NOT NULL,
    relationship VARCHAR(100),
    phone VARCHAR(20) NOT NULL,
    email VARCHAR(255),
    is_primary BOOLEAN DEFAULT false,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

## 🔌 APIs Principais

### Autenticação
```
POST   /api/auth/register
POST   /api/auth/login
POST   /api/auth/refresh-token
POST   /api/auth/forgot-password
POST   /api/auth/reset-password
GET    /api/auth/verify-email/:token
```

### Usuário
```
GET    /api/users/profile
PUT    /api/users/profile
DELETE /api/users/account
POST   /api/users/profile-picture
```

### Diário
```
GET    /api/diary/entries
POST   /api/diary/entries
GET    /api/diary/entries/:id
PUT    /api/diary/entries/:id
DELETE /api/diary/entries/:id
GET    /api/diary/statistics
```

### Caixinha das Emoções
```
GET    /api/emotion-box/items
POST   /api/emotion-box/items
GET    /api/emotion-box/items/:id
PUT    /api/emotion-box/items/:id
DELETE /api/emotion-box/items/:id
GET    /api/emotion-box/random
```

### Emoções
```
GET    /api/emotions
POST   /api/emotions
GET    /api/emotions/analytics
GET    /api/emotions/trends
```

### Emergências
```
GET    /api/emergency/resources
GET    /api/emergency/resources/:id
GET    /api/emergency/contacts
POST   /api/emergency/contacts
PUT    /api/emergency/contacts/:id
DELETE /api/emergency/contacts/:id
POST   /api/emergency/alert (notifica contatos)
```

### Assinaturas
```
GET    /api/subscriptions/plans
POST   /api/subscriptions/subscribe
GET    /api/subscriptions/current
PUT    /api/subscriptions/cancel
POST   /api/subscriptions/reactivate
POST   /api/subscriptions/webhook (pagamento)
```

---

## 🎨 Funcionalidades Detalhadas

### 1. Diário Emocional
- Entrada de texto livre com rich text
- Anexar fotos e áudios
- Categorização por humor (escala 1-10)
- Tags personalizadas
- Busca e filtros avançados
- Estatísticas e gráficos de humor ao longo do tempo
- Lembretes para escrever

### 2. Caixinha das Emoções
- Repositório pessoal de conteúdo positivo
- Tipos: frases motivacionais, fotos, músicas, vídeos
- Categorias: calma, motivação, reflexão
- Acesso aleatório para momentos difíceis
- Compartilhamento opcional com terapeuta

### 3. Emergências Emocionais
- SOS button em destaque
- Recursos de crise imediatos:
    - Técnicas de respiração guiadas
    - Exercícios de grounding
    - Lista de contatos de emergência
    - Linhas de apoio (CVV, etc)
- Contatos de confiança configuráveis
- Botão de alerta rápido

### 4. Sistema de Assinaturas

**Plano Gratuito**
- Diário com limite de 10 entradas/mês
- Caixinha com 5 itens
- Recursos de emergência básicos

**Plano Premium (Mensal/Anual)**
- Diário ilimitado
- Caixinha ilimitada
- Estatísticas avançadas
- Export de dados
- Backup automático
- Sem anúncios

---

## 🔒 Segurança e Privacidade

### Implementações Essenciais
1. **Criptografia end-to-end** para dados sensíveis
2. **LGPD compliance**: consentimento, portabilidade, exclusão
3. **JWT** com refresh tokens
4. **HTTPS** obrigatório
5. **Rate limiting** nas APIs
6. **Validação rigorosa** de inputs
7. **Backup automático** criptografado
8. **Logs de auditoria** (sem dados sensíveis)

---

## 📊 Integrações Futuras

- Gateway de pagamento (Stripe/PagSeguro)
- Notificações push (Firebase Cloud Messaging)
- Analytics (Google Analytics/Mixpanel)
- Crash reporting (Sentry)
- Email service (SendGrid/AWS SES)
- Cloud storage (AWS S3/GCS)

---

## 🚀 Roadmap de Desenvolvimento

### Fase 1 - MVP (2-3 meses)
- [ ] Setup da infraestrutura
- [ ] Sistema de autenticação
- [ ] Diário básico
- [ ] Caixinha das emoções
- [ ] Recursos de emergência
- [ ] UI/UX fundamental

### Fase 2 - Monetização (1-2 meses)
- [ ] Sistema de assinaturas
- [ ] Integração com pagamentos
- [ ] Planos free e premium
- [ ] Dashboard administrativo

### Fase 3 - Melhorias (2-3 meses)
- [ ] Estatísticas e analytics
- [ ] Export de dados
- [ ] Temas personalizáveis
- [ ] Notificações inteligentes
- [ ] Backup e sincronização

### Fase 4 - Expansão (futuro)
- [ ] Integração com profissionais
- [ ] Teleconsulta
- [ ] Comunidade (moderada)
- [ ] Gamificação
- [ ] Machine learning para insights

---

## 📝 Comandos Úteis

### Backend
```bash
# Criar projeto Spring Boot
spring init --dependencies=web,data-jpa,security,postgresql psique-backend

# Rodar localmente
./mvnw spring-boot:run

# Build
./mvnw clean package

# Testes
./mvnw test
```

### Frontend
```bash
# Criar projeto Flutter
flutter create psique_app

# Rodar
flutter run

# Build Android
flutter build apk --release

# Build iOS
flutter build ios --release

# Testes
flutter test
```

---

## 🌍 Variáveis de Ambiente

```env
# Database
DB_HOST=localhost
DB_PORT=5432
DB_NAME=psique_db
DB_USER=postgres
DB_PASSWORD=senha_segura

# JWT
JWT_SECRET=sua_chave_secreta_muito_longa
JWT_EXPIRATION=86400000

# Cloud Storage
AWS_ACCESS_KEY=sua_access_key
AWS_SECRET_KEY=sua_secret_key
AWS_BUCKET=psique-storage

# Payment Gateway
STRIPE_API_KEY=sk_test_xxx
STRIPE_WEBHOOK_SECRET=whsec_xxx

# Email
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=seu_email
SMTP_PASSWORD=sua_senha
```

---

## 📄 Licença e Autoria

**Criado por:** Andreia Lima Girão
**Data:** Outubro 2025
**Versão:** 1.0.0

---

## 📞 Próximos Passos

1. **Escolher nome definitivo** do app
2. **Definir identidade visual** (logo, cores, tipografia)
3. **Criar repositórios Git**
4. **Setup do ambiente de desenvolvimento**
5. **Iniciar com Claude Code** seguindo esta estrutura
6. **Desenvolver protótipos no Figma** (opcional)
7. **Registrar domínio e redes sociais**

---

**Dica para Claude Code:**
Use este documento como referência e comece pelo backend, criando primeiro:
1. Models e entidades
2. Repositories
3. Services básicos
4. Controllers de autenticação
5. Testes unitários

Boa sorte com o projeto! 🚀