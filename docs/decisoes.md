# Decisões de produto

Registro das decisões tomadas na fase de design, com o motivo de cada uma. Decisão nova entra no topo da seção correspondente.

## Produto e negócio

| Decisão | Motivo |
| --- | --- |
| Stack, padrões de projeto e skills **iguais aos do GetCart** | Reaproveita o que já funciona e o que o time e os agentes já conhecem. Detalhes em [`stack.md`](stack.md). |
| Nome **Vera** | Nome feminino, curto, que remete a "verdadeiro": o retrato real da carteira contra o ideal. "Prumo" foi descartado por conflito com a Prumo Logística. Disponibilidade de domínio e INPI ainda não checada. |
| Licença **AGPL-3.0** | Impede que alguém feche o código e ofereça como serviço sem publicar as mudanças. |
| Open source e gratuito | O objetivo é relevância e marca pessoal, não receita. |
| Versão hospedada pela Revtriever | Investidor comum não sobe servidor; sem versão hospedada, só desenvolvedores usariam. |
| Concorrência relevante = outros open source | Os pagos (Kinvo, Gorila) não disputam o mesmo objetivo. |

## Gestão patrimonial

| Decisão | Motivo |
| --- | --- |
| Uma carteira por conta, sem "de quem" | Simplicidade: o que importa é a distribuição do patrimônio, não o dono de cada posição. |
| Cadastro manual | Não há forma gratuita e confiável de puxar posições de todas as corretoras, bancos de fora e exchanges. |
| Renda variável só com posição (quantidade) | Registrar transações exigiria tratar eventos corporativos (desdobramento, grupamento, bonificação), complexidade que não serve à visão de alocação. |
| Renda fixa com valorização automática | Atualizar saldo à mão é chato demais; o valor aproximado na curva é melhor do que nenhum. |
| Tesouro Direto separado de CDB/LCI no cadastro | Tesouro tem preço oficial diário: basta a quantidade. Os outros títulos precisam de aplicação, taxa e datas. |
| Classificação por exposição, editável, sem IA | IVVB11 é ação dos EUA, mesmo negociado na B3. Classificação determinística é grátis e previsível. |
| Mapa curado de ETFs no repositório | A comunidade corrige por PR, de graça. |
| Carteira-alvo em duas camadas | Classe (ex.: 25% em ações EUA) e ativo dentro da classe (ex.: 30% ITUB4, 40% WEGE3, 30% PETR4). |
| Aporte inteligente como diferencial | Investidor de longo prazo não vende para rebalancear; a pergunta mensal é "onde coloco este dinheiro". |
| Não permitir o mesmo ativo duas vezes | Evita posições duplicadas que distorcem a distribuição; leva à posição existente para editar a quantidade. Renda fixa é exceção (títulos distintos). |
| Exportar carteira em planilha | Os dados são do usuário. |

## Gestão de gastos

| Decisão | Motivo |
| --- | --- |
| Open Finance via Meu Pluggy com credencial do usuário, hospedagem nossa | Acesso comercial custa milhares de reais por mês; com a conta gratuita de cada pessoa, o custo para nós é zero. |
| Importação OFX/CSV como alternativa | Funciona com qualquer banco e é plano B se o Meu Pluggy mudar. |
| Classificação sem IA | Categoria do agregador + dicionário curado + regras aprendidas cobrem a maior parte; IA só opcional. |
| Sugestão de corte determinística | É matemática: meta contra realizado, categorias flexíveis contra a média do próprio usuário. |
| Exportar transações em planilha | Os dados são do usuário. |

## Plataforma

| Decisão | Motivo |
| --- | --- |
| Um ambiente só (produção), com AWS CDK no formato do GetCart | Projeto open source sem receita: um ambiente de dev dobraria o custo de infraestrutura sem necessidade. A validação acontece localmente e na CI. |
| Login só social (Google e Facebook) | Não guardar senha própria reduz a superfície de ataque e o atrito no cadastro. |
| Login separado da landing page | O login fica só login; a explicação do produto vai para a LP. |
| Onboarding com duas etapas opcionais | Ativos (~5 min) e bancos (~15 min), cada uma explicando por que existe; quem pula cai em estados vazios que mostram o próximo passo. |
| Ativos antes de bancos no onboarding | A etapa mais rápida primeiro, com resultado imediato, aumenta a chance de completar. |
| Identidade visual: tema claro, base rosa | Diferencia de apps financeiros sóbrios e conversa com o nome feminino. |
