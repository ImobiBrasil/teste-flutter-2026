---
title: Teste Técnico — Desenvolvedor Flutter Pleno
date: 2026-03-20
---

# Teste Técnico — Desenvolvedor Flutter Pleno

## Sumário

- [Sobre o Teste](#sobre-o-teste)
- [O Desafio](#o-desafio)
- [Identidade Visual](#identidade-visual)
- [Requisitos Funcionais](#requisitos-funcionais)
- [Requisitos Técnicos](#requisitos-técnicos)
- [API Simulada](#api-simulada)
- [Diferenciais](#diferenciais)
- [O Que Será Avaliado](#o-que-será-avaliado)
- [Entrega](#entrega)

---

## Sobre o Teste

Tempo estimado: **2 a 3 horas**. Não esperamos um app perfeito — queremos ver como você organiza código, toma decisões de arquitetura e resolve problemas reais.

Formato: take-home. Faça no seu ritmo, dentro do prazo combinado.

---

## O Desafio

Construir um mini app de **listagem e detalhe de imóveis**, simulando uma versão simplificada do que fazemos na ImobiBrasil.

O app deve consumir uma API REST (fornecida abaixo como JSON mockado), exibir uma lista de imóveis com busca/filtro e permitir visualizar os detalhes de cada imóvel.

---

## Identidade Visual

O app deve seguir a identidade visual da ImobiBrasil. Use os recursos abaixo:

**Logotipo completo (para splash screen ou AppBar):**
`https://imobibrasil.com.br/imagens/logotipo/svg/logo-original-imobibrasil.svg`

**Ícone (para favicon, ícone do app ou elementos menores):**
`https://imobibrasil.com.br/imagens/logotipo/svg/icone-original-imobibrasil.svg`

**Paleta de cores:**

| Uso | Cor | Hex |
|---|---|---|
| Primária (botões, AppBar, destaques) | Verde ImobiBrasil | `#1B7A43` |
| Primária escura (status bar, hover) | Verde escuro | `#145C32` |
| Secundária (badges, links, ações secundárias) | Azul | `#1A73E8` |
| Fundo | Cinza claro | `#F5F5F5` |
| Texto principal | Cinza escuro | `#212121` |
| Texto secundário | Cinza médio | `#757575` |

Não é necessário seguir a paleta ao pixel — o objetivo é que o app tenha a cara da ImobiBrasil.

---

## Requisitos Funcionais

### Tela 1 — Lista de Imóveis

- Exibir cards com: foto principal, título, cidade, preço e tipo (venda/aluguel)
- Campo de busca por texto (filtrar por título ou cidade)
- Filtro por tipo: Todos, Venda, Aluguel
- Loading state enquanto os dados carregam
- Estado vazio quando o filtro não retorna resultados

### Tela 2 — Detalhe do Imóvel

- Foto principal em destaque
- Título, descrição, preço formatado em BRL, cidade e bairro
- Características: quartos, banheiros, vagas, área (m²)
- Botão "Entrar em Contato" (pode apenas exibir um SnackBar ou dialog — não precisa funcionar de verdade)

### Tela 3 — Edição do Imóvel

- Acessível a partir da tela de detalhe (botão "Editar" ou ícone de lápis)
- Formulário com os campos editáveis: título, descrição, tipo (dropdown: venda/aluguel), preço, cidade, bairro, quartos, banheiros, vagas, área (m²)
- Validação básica: campos obrigatórios não podem ficar vazios, preço e área devem ser numéricos e maiores que zero
- Ao salvar, atualizar o estado local do app (a alteração deve refletir na lista e no detalhe)
- Feedback visual ao salvar (SnackBar de confirmação)
- Botão de cancelar que descarta as alterações e volta ao detalhe

### Navegação

- Transição da lista para o detalhe ao tocar no card
- Transição do detalhe para a edição ao tocar em "Editar"
- Botão de voltar no detalhe e na edição

---

## Requisitos Técnicos

- Flutter 3.x com Dart
- Gerenciamento de estado: usar **Riverpod**, **BLoC** ou **Provider** (justificar a escolha no README)
- Separação de camadas: no mínimo, separar UI, lógica de negócio e acesso a dados
- Tratar estados de loading e erro na UI
- Código limpo, com nomes claros e organização de pastas coerente

---

## API Simulada

Usar o JSON abaixo como fonte de dados. Pode ser servido localmente, lido de um arquivo asset ou consumido via um mock HTTP. Simule um delay de 1-2 segundos para testar o loading state.

```json
{
  "imoveis": [
    {
      "id": 1,
      "titulo": "Apartamento Centro",
      "descricao": "Apartamento de 2 quartos no centro da cidade, próximo ao comércio e transporte público. Reformado recentemente com acabamento moderno.",
      "tipo": "aluguel",
      "preco": 1800.00,
      "cidade": "Presidente Prudente",
      "bairro": "Centro",
      "quartos": 2,
      "banheiros": 1,
      "vagas": 1,
      "area_m2": 65,
      "foto": "https://picsum.photos/seed/apt1/600/400"
    },
    {
      "id": 2,
      "titulo": "Casa Jardim Bongiovani",
      "descricao": "Casa ampla com 3 quartos, quintal e churrasqueira. Rua tranquila em bairro residencial consolidado.",
      "tipo": "venda",
      "preco": 420000.00,
      "cidade": "Presidente Prudente",
      "bairro": "Jardim Bongiovani",
      "quartos": 3,
      "banheiros": 2,
      "vagas": 2,
      "area_m2": 150,
      "foto": "https://picsum.photos/seed/casa2/600/400"
    },
    {
      "id": 3,
      "titulo": "Kitnet Universitária",
      "descricao": "Kitnet mobiliada próxima à Unesp. Ideal para estudantes. Inclui água e internet no valor.",
      "tipo": "aluguel",
      "preco": 850.00,
      "cidade": "Presidente Prudente",
      "bairro": "Vila Santa Helena",
      "quartos": 1,
      "banheiros": 1,
      "vagas": 0,
      "area_m2": 28,
      "foto": "https://picsum.photos/seed/kit3/600/400"
    },
    {
      "id": 4,
      "titulo": "Sobrado Vila Marcondes",
      "descricao": "Sobrado comercial e residencial com 4 quartos e ponto comercial no térreo. Boa localização com alto fluxo.",
      "tipo": "venda",
      "preco": 580000.00,
      "cidade": "Presidente Prudente",
      "bairro": "Vila Marcondes",
      "quartos": 4,
      "banheiros": 3,
      "vagas": 2,
      "area_m2": 200,
      "foto": "https://picsum.photos/seed/sobrado4/600/400"
    },
    {
      "id": 5,
      "titulo": "Chácara Montalvão",
      "descricao": "Chácara de 2.000m² com piscina, pomar e casa sede de 3 quartos. Acesso pavimentado a 10 minutos do centro.",
      "tipo": "venda",
      "preco": 350000.00,
      "cidade": "Presidente Prudente",
      "bairro": "Montalvão",
      "quartos": 3,
      "banheiros": 2,
      "vagas": 4,
      "area_m2": 2000,
      "foto": "https://picsum.photos/seed/chacara5/600/400"
    },
    {
      "id": 6,
      "titulo": "Sala Comercial Ed. Corporate",
      "descricao": "Sala de 40m² no edifício Corporate, 8º andar. Ar-condicionado central, recepção e segurança 24h.",
      "tipo": "aluguel",
      "preco": 2200.00,
      "cidade": "Presidente Prudente",
      "bairro": "Centro",
      "quartos": 0,
      "banheiros": 1,
      "vagas": 1,
      "area_m2": 40,
      "foto": "https://picsum.photos/seed/sala6/600/400"
    }
  ]
}
```

---

## Diferenciais (Extras)

Não são obrigatórios, mas fazem diferença real na avaliação. Candidatos que entregam extras demonstram autonomia e vontade de ir além — qualidades que valorizamos na ImobiBrasil.

### Login Simples

- Tela de login com e-mail e senha (validação local, sem backend real)
- Credenciais fixas para teste: `corretor@imobibrasil.com.br` / `imobi2026`
- Após login, redirecionar para a lista de imóveis
- Exibir nome do usuário logado na AppBar ou drawer
- Botão de logout que volta à tela de login
- Proteger as rotas: sem login, não acessa lista/detalhe/edição

### Cadastro de Novo Imóvel

- Botão "Adicionar Imóvel" na tela de lista (FAB ou botão na AppBar)
- Formulário com os mesmos campos da edição: título, descrição, tipo, preço, cidade, bairro, quartos, banheiros, vagas, área
- Gerar um `id` incremental automaticamente
- Usar uma foto placeholder (ex: `https://picsum.photos/seed/novo/600/400`)
- Validação dos campos obrigatórios
- Ao salvar, o novo imóvel deve aparecer na lista imediatamente

### Outros Extras


- **Firebase:** integração simples com Firebase Analytics ou Crashlytics (pode ser só a inicialização)
- **Animações:** hero animation na transição lista → detalhe, ou shimmer no loading
- **Persistência local:** salvar dados com SharedPreferences, Hive ou SQLite para que alterações sobrevivam ao restart do app

---

## O Que Será Avaliado

| Critério | Peso | O que olhamos |
|---|---|---|
| Arquitetura e organização | Alto | Separação de camadas, estrutura de pastas, injeção de dependências |
| Qualidade do código | Alto | Nomes claros, funções pequenas, sem código morto, DRY |
| UI e UX | Médio | Fidelidade visual à marca, estados de loading/erro/vazio, formatação de valores |
| Integração com dados | Médio | Consumo do JSON, parsing, tratamento de erros, mutação de estado |
| Extras e diferenciais | Médio | Login, cadastro de imóvel, testes, CI, Firebase, animações, persistência |
| README e documentação | Baixo | Decisões técnicas explicadas, instruções de setup claras |

---

## Entrega

1. Criar um repositório **publico** no GitHub
2. Incluir um `README.md` com:
   - Instruções de como rodar o projeto
   - Decisões técnicas tomadas (gerenciamento de estado, arquitetura, libs usadas)
   - O que você faria diferente com mais tempo
3. Enviar o link do repositório no formulário indicado


---

Boa sorte. Estamos curiosos pra ver o que você vai construir.
