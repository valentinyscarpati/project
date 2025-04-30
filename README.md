
# 🌡️ API de Monitoramento de Temperaturas

Esta API permite gerenciar locais e registrar medições de temperatura, com funcionalidades de listagem, filtros e um dashboard com estatísticas.

---

## 🚀 Como rodar localmente

### Pré-requisitos

- Node.js (versão 16+)
- MySQL
- Git

### Passos

```bash
# Clone o repositório
git clone https://github.com/andrerribeiroo/project.git
cd seurepositorio/server

# Instale as dependências
npm install

# Configure o banco de dados em config/database.js
# Exemplo:
# const pool = mysql.createPool({
#   host: 'localhost',
#   user: 'root',
#   password: 'sua_senha',
#   database: 'temperaturas',
# });

# Inicie o servidor
npm start
```

Servidor disponível em `http://localhost:3000`

---

## 📚 Documentação da API

### 📊 Dashboard

#### `GET /`

Retorna estatísticas gerais do sistema.

**Resposta:**
```json
{
  "totalLocais": 5,
  "totalTemperaturas": 120,
  "mediaTemperatura": 22.3,
  "ultimasMedicoes": [
    {
      "id": 1,
      "id_local": 2,
      "temperatura": 23.4,
      "data": "2025-04-22",
      "horario": "14:00:00",
      "local_nome": "Sala 1"
    }
  ]
}
```

---

### 📍 Locais

#### `GET /locais`
Lista todos os locais.

#### `GET /locais/:id`
Busca um local pelo ID.

#### `POST /locais`
Cria um novo local.

**Exemplo de body:**
```json
{
  "nome": "Laboratório",
  "estado": "SP",
  "pais": "Brasil"
}
```

#### `PUT /locais/:id`
Atualiza um local.

#### `DELETE /locais/:id`
Remove um local.

---

### 🌡️ Temperaturas

#### `GET /temperaturas`
Lista medições com filtros opcionais:

- `startDate=YYYY-MM-DD`
- `endDate=YYYY-MM-DD`
- `locationId=1`

#### `GET /temperaturas/:id`
Busca uma medição específica.

#### `POST /temperaturas`
Registra nova medição.

**Exemplo de body:**
```json
{
  "data": "2025-04-23",
  "horario": "15:30:00",
  "temperatura": 24.1,
  "id_local": 1
}
```

#### `PUT /temperaturas/:id`
Atualiza uma medição.

#### `DELETE /temperaturas/:id`
Remove uma medição.
