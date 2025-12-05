# PromoBlix

**PromoBlix** é uma plataforma SaaS multi-idioma para automação de marketing de afiliados que gera e publica conteúdo promocional automaticamente.

## 🚀 Stack Tecnológica

- **Laravel 11** - Framework PHP
- **Filament v4.3** - Admin Panel
- **PHP 8.4** com extensão `intl`
- **MySQL 8.0** - Banco de dados
- **Redis** - Cache e queues
- **Nginx** - Web server
- **Docker & Docker Compose** - Containerização

## 📋 Pré-requisitos

- Docker e Docker Compose instalados
- Git configurado com SSH para GitHub

## 🛠️ Instalação e Configuração

### 1. Clone o repositório

```bash
git clone git@github.com:jonatanfroes/promoblix.git
cd promoblix
```

### 2. Configure o ambiente

```bash
cp .env.example .env
```

### 3. Construa e inicie os containers Docker

```bash
docker-compose build
docker-compose up -d
```

### 4. Instale as dependências e configure a aplicação

```bash
# Gerar chave da aplicação
docker-compose exec -u promoblix app php artisan key:generate

# Executar migrações
docker-compose exec -u promoblix app php artisan migrate

# Criar usuário admin
docker-compose exec -u promoblix app php artisan make:filament-user
```

## 🌐 Acessar a Aplicação

- **Frontend**: [http://localhost:8000](http://localhost:8000)
- **Admin Panel**: [http://localhost:8000/adminadmin/login](http://localhost:8000/adminadmin/login)

### Credenciais Padrão

- **Email**: admin@promoblix.com
- **Senha**: password

## 🐳 Comandos Docker Úteis

```bash
# Iniciar containers
docker-compose up -d

# Parar containers
docker-compose down

# Ver logs
docker-compose logs -f app

# Acessar container PHP
docker-compose exec -u promoblix app bash

# Executar comandos Artisan
docker-compose exec -u promoblix app php artisan <comando>

# Executar Composer
docker-compose exec -u promoblix app composer <comando>
```

## 📦 Estrutura Docker

```
docker/
├── nginx/          # Configuração Nginx
│   └── default.conf
├── php/            # PHP 8.4 + extensões
│   ├── Dockerfile
│   └── local.ini
└── mysql/          # Dados MySQL (ignorados no git)
    └── data/
```

## 🔧 Serviços Docker

| Serviço | Container | Porta | Descrição |
|---------|-----------|-------|-----------|
| app | promoblix_app | 9000 | PHP-FPM 8.4 |
| nginx | promoblix_nginx | 8000 | Web Server |
| mysql | promoblix_mysql | 3306 | MySQL 8.0 |
| redis | promoblix_redis | 6379 | Cache/Queue |
| node | promoblix_node | - | Node.js 20 (Vite) |

## 🌍 Multi-idioma

O projeto está configurado para suportar múltiplos idiomas:
- **Português (Brasil)** - pt_BR (padrão)
- **Inglês** - en
- **Espanhol** - es

## 📝 Próximos Passos

- [ ] Implementar módulos de scraping
- [ ] Integração com OpenAI/Claude para geração de textos
- [ ] Integração com DALL-E/Stable Diffusion para geração de imagens
- [ ] API Instagram para publicação
- [ ] API WhatsApp Business para grupos
- [ ] Sistema de analytics
- [ ] Integração Stripe e Hotmart (monetização)

## 🤝 Contribuindo

Este é um projeto privado em desenvolvimento ativo.

## 📄 Licença

Proprietary - Todos os direitos reservados

---

**Desenvolvido com ❤️ usando Laravel + Filament**
