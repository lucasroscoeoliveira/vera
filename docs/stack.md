# Stack e padrões

A Vera usa a mesma stack, os mesmos padrões de projeto e as mesmas skills de agente do GetCart. Não há decisão nova aqui: quando houver dúvida, vale o que o GetCart faz.

## Organização dos repositórios

| Repositório | Papel |
| --- | --- |
| `vera` (este) | Documentação de produto, decisões e protótipo |
| `vera-api` | Back-end |
| `vera-fe` | Aplicação web |
| `vera-site` | Landing page |

## Back-end (`vera-api`)

- **NestJS + TypeScript**, Node 22
- **Arquitetura em camadas** `controller → application → domain → repository`, com ports (classes abstratas) para inversão de dependência. As fronteiras são verificadas pelo ESLint (`eslint-plugin-boundaries`), não pela memória de quem revisa.
- **Postgres + Kysely** (migrations e tipos gerados com `kysely-codegen`)
- **Zod** para validação (`nestjs-zod`) e **OpenAPI** gerado a partir dos DTOs
- **BullMQ + Redis** para filas e jobs agendados (cotações diárias, sincronização de extratos)
- **pino + OpenTelemetry** para logs, traces e métricas; **PostHog** para produto
- **Vitest + Testcontainers** (Postgres, Redis) para testes de integração
- **AWS CDK** para infraestrutura, no mesmo formato do GetCart

## Front-end (`vera-fe`)

- **React 19 + TypeScript strict + Vite**
- **TanStack Router** (rotas por arquivo, tipadas) e **TanStack Query**
- **Tailwind v4 + Radix**, ícones `lucide-react`
- **react-hook-form + Zod** para formulários
- **openapi-typescript + openapi-fetch**: o cliente da API é gerado a partir do OpenAPI do back-end
- **i18next** desde o primeiro dia: nenhum texto de interface fixo em pt-BR
- **Vitest + Testing Library + MSW**
- Organização por feature (`features/<feature>/{api,components,pages,lib,schemas}`) com fronteiras verificadas pelo ESLint

## Landing page (`vera-site`)

- **Astro**, como os sites dos outros produtos

## Ambientes

Diferente do GetCart, a Vera tem **um ambiente só: produção**. Não existe ambiente de dev.

- Infraestrutura em AWS CDK, do mesmo jeito que o GetCart, mas com uma única stack de produção.
- Uma branch principal (`main`); sem branch `development` e sem o fluxo de mergeback.
- CI com um único workflow de deploy (`deploy-prod`); os workflows `deploy-dev` e `mergeback-development` do GetCart não são copiados.
- Validação antes de produção acontece localmente (Docker Compose) e nos testes da CI.

## Convenções gerais

- **Idioma por público:** código, identificadores, rotas, logs e skills em inglês; regras de negócio, decisões, commits, issues e PRs em pt-BR; interface do usuário via i18n.
- **Commits** no padrão Conventional Commits (commitlint + husky + lint-staged)
- **Prettier + ESLint** em todos os repositórios; **SonarQube** na CI
- **Skills de agente** em `.claude/skills/` de cada repositório, adaptadas das skills do GetCart

## Ponto de atenção: hospedagem própria

O GetCart depende de serviços da AWS (SQS, SES) que não existem numa instalação doméstica. Como a Vera precisa rodar com Docker Compose para quem quiser hospedar sozinho, cada dependência de nuvem precisa de uma alternativa local ou de um adaptador atrás de um port. Filas e jobs já usam BullMQ + Redis, que roda em qualquer lugar.
