# PokeSystem 

[![Python Version](https://img.shields.io/badge/python-3.10%2B-blue.svg)](https://www.python.org/)
[![API](https://img.shields.io/badge/API-PokeAPI-red.svg)](https://pokeapi.co/)

Sistema de gerenciamento de usuários e coleções de Pokémon com integração direta à PokeAPI. O projeto demonstra padrões de POO (Programação Orientada a Objetos), consumo de APIs REST e manipulação de estados em memória.

## 📌 Funcionalidades Core

* **Gestão de Usuários:** Criação, exclusão e autenticação (simulada).
* **Integração PokeAPI:** Busca dinâmica de dados (tipos, status, altura, peso e movimentos).
* **Coleção Inteligente:** Sistema de inventário que agrupa Pokémon repetidos e controla quantidades.
* **Sistema de Favoritos:** Regra de negócio exclusiva para definição de um Pokémon destaque por usuário.
* **Proteção de Dados:** Validação de exclusão para Pokémons marcados como favoritos (exige confirmação).

---

## 🛠️ Arquitetura e Classes

O sistema foi desenhado seguindo o princípio da responsabilidade única:

### 1. `Pokemon` (Data Provider)
Responsável pelo parse da API externa.
* **Static Method `from_api`**: Centraliza o tratamento de erros de rede (HTTP 404/500) e normaliza unidades de medida (decímetros para metros, hectogramas para quilogramas).

### 2. `Usuario` (Model)
Entidade que carrega o estado do jogador.
* `colecao`: Implementada como Hash Map (`Dict[int, dict]`) para garantir performance de busca.
* `favorito_id`: Referência opcional para um ID presente ou não na coleção ativa.

### 3. `PokeSystem` (Service/Controller)
Orquestrador das regras de negócio.
* Gerencia o dicionário global de usuários.
* Controla o fluxo de entrada/saída de dados e interações via terminal.

---

## 🚀 Instalação e Uso

### Pré-requisitos
* Python 3.10 ou superior.
* Biblioteca `requests`.

```bash
# Instalar dependência
pip install requests