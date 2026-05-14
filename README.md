# 🐾 Sistema Veterinário - Microsserviço de Agendamentos

<div align="center">

![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![Spring Data JPA](https://img.shields.io/badge/Spring%20Data%20JPA-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![Status](https://img.shields.io/badge/Status-Em%20Desenvolvimento-yellow?style=for-the-badge)

**Microsserviço responsável pelo agendamento e controle de consultas veterinárias, parte integrante do Sistema Veterinário desenvolvido em arquitetura de microsserviços.**

</div>

---

## 📋 Sobre o Projeto

Este repositório contém o **microsserviço de Agendamentos**, como parte de um sistema veterinário distribuído em arquitetura de microsserviços.

O sistema completo é composto por três repositórios independentes, cada um mantido por um(a) integrante da equipe, que se comunicam entre si via **APIs REST**:

| Microsserviço | Responsável | Repositório |
|---|---|---|
| 📅 **Agendamentos** | Gabriel Rolim | ← este repositório |
| 🐶 **Pets** | Rayssa Fialho | repositório separado |
| 👤 **Tutores** | Luana Oliveira | repositório separado |

---

## 📅 Microsserviço de Agendamentos

Responsável pelo gerenciamento completo das consultas veterinárias, expondo uma **API REST** consumida tanto pela interface web quanto pelos demais microsserviços.

### ✅ Funcionalidades

- Agendamento de consultas
- Atualização de agendamentos
- Cancelamento de agendamentos
- Consulta de histórico
- Listagem de agendamentos

### 📦 Modelo de Dados

| Campo | Tipo | Descrição |
|---|---|---|
| `id_agendamento` | PK | Identificador único do agendamento |
| `data` | — | Data da consulta |
| `hora` | — | Horário da consulta |
| `motivo_consulta` | — | Motivo do atendimento |
| `id_tutor` | FK | Referência ao tutor responsável |
| `id_pet` | FK | Referência ao animal |

### 🌐 Interface Web

Página **HTML/CSS** integrada ao backend via **fetch API**, permitindo realizar todas as operações de CRUD pelo navegador sem ferramentas externas.

| Operação | Descrição |
|---|---|
| ➕ **Create** | Agendamento de nova consulta via formulário |
| 📋 **Read** | Listagem e visualização dos agendamentos |
| ✏️ **Update** | Edição de um agendamento existente |
| 🗑️ **Delete** | Cancelamento de um agendamento |

---

## 🔗 Integração com os Demais Microsserviços

Embora cada serviço seja independente e possua seu próprio repositório, eles se complementam e interagem via **APIs REST** para garantir a integridade dos dados em todo o sistema.

O microsserviço de Agendamentos é o **serviço mais dependente** do sistema — ele consome as APIs de Pets e de Tutores para validar os dados antes de confirmar qualquer agendamento, uma vez que utiliza tanto `id_pet` quanto `id_tutor` como chaves estrangeiras.

### 🐶 Serviço de Pets — Rayssa Fialho
Antes de confirmar um agendamento, o serviço consulta a API de Pets para verificar se o animal informado está cadastrado no sistema.

```
┌──────────────────┐     REST API     ┌────────────────┐
│   Agendamentos   │ ──────────────▶  │     Pets       │
│   (G. Rolim)     │   valida pet     │  (R. Fialho)   │
└──────────────────┘                  └────────────────┘
```

### 👤 Serviço de Tutores — Luana Oliveira
Antes de confirmar um agendamento, o serviço consulta a API de Tutores para verificar se o tutor responsável está cadastrado no sistema.

```
┌──────────────────┐     REST API     ┌────────────────┐
│   Agendamentos   │ ──────────────▶  │    Tutores     │
│   (G. Rolim)     │  valida tutor    │  (L. Oliveira) │
└──────────────────┘                  └────────────────┘
```

> 💡 Caso o pet ou o tutor informado não existam em seus respectivos serviços, o agendamento não é realizado, garantindo a **consistência dos dados** entre os microsserviços.

---

## 🛠️ Tecnologias Utilizadas

### Backend
| Tecnologia | Finalidade |
|---|---|
| **Java** | Linguagem principal de desenvolvimento |
| **Spring Boot** | Framework para criação do microsserviço |
| **Spring Data JPA** | Persistência e mapeamento de dados |
| **MySQL** | Banco de dados relacional |
| **Maven** | Gerenciamento de dependências |

### Frontend
| Tecnologia | Finalidade |
|---|---|
| **HTML5** | Estrutura da página de CRUD |
| **CSS3** | Estilização da interface web |

### Outros
| Tecnologia | Finalidade |
|---|---|
| **GitHub** | Controle de versão e colaboração |

---

<div align="center">

✨ **Projeto acadêmico desenvolvido para estudo de Arquitetura de Microsserviços**


</div>
