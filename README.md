# Vera

**O retrato real do seu dinheiro.** Plataforma financeira open source e gratuita com dois objetivos:

1. **Gestão patrimonial:** ver em segundos como os investimentos estão distribuídos (Brasil, EUA e cripto, numa moeda só), comparar com a carteira que você considera ideal e saber onde aportar.
2. **Gestão de gastos:** receber os gastos do cartão e da conta pelo Open Finance, categorizados, e ver onde cortar para bater a meta de economia.

> Status: **fase de design**. O repositório tem a análise de viabilidade, as decisões de produto e um protótipo navegável. Nada da aplicação foi implementado ainda.

## O que tem aqui

| Caminho | Conteúdo |
| --- | --- |
| [`docs/viabilidade.md`](docs/viabilidade.md) | Análise de viabilidade técnica e de negócio dos dois módulos |
| [`docs/decisoes.md`](docs/decisoes.md) | Registro das decisões de produto, com o motivo de cada uma |
| [`prototipo/`](prototipo/) | Protótipo navegável em um único HTML, com dados de exemplo |

O trabalho está organizado no [Project da Vera](https://github.com/users/lucasroscoeoliveira/projects), um card por entrega.

## Protótipo

Abra `prototipo/index.html` no navegador. Não precisa de build nem de servidor. Ele cobre:

- Login social (Google e Facebook, simulado)
- Onboarding com duas etapas opcionais: cadastrar ativos e conectar bancos
- Visão geral da carteira, carteira-alvo em duas camadas e aporte inteligente
- Cadastro de ativos por tipo, com renda fixa calculada automaticamente
- Resumo de gastos, transações com regras de categoria, sugestão de corte e conexões

Todos os valores são de exemplo; nada é salvo.

## Princípios

- **Gratuito de verdade.** Nenhuma fonte de dados cobra por usuário: cotações são por ativo e ficam em cache, e o Open Finance usa a conta gratuita de cada pessoa no Meu Pluggy.
- **Sem IA obrigatória.** Classificação de ativos e de gastos é determinística; IA, se entrar, é opcional e com a chave do próprio usuário.
- **Seus dados, seu controle.** Código aberto, login sem senha própria, credenciais cifradas e possibilidade de rodar tudo no seu servidor.

## Licença

[AGPL-3.0](LICENSE). Quem oferecer uma versão modificada como serviço precisa publicar o código dessa versão.

Mantido por [Lucas Oliveira](https://github.com/lucasroscoeoliveira). A versão hospedada é operada pela Revtriever.
