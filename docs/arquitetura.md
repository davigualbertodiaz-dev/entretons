# Arquitetura e padrões técnicos

Estas são as recomendações padrão da squad. Antes de começar a codar, confirme com o desenvolvedor, porque a escolha depende do nível dele. Registre a decisão final como ADR no fim deste arquivo (ou peça ao desenvolvedor para registrar no repositório dele).

## Stack sugerida (a confirmar)

- **Front-end:** React com Next.js e TypeScript, estilizado com Tailwind CSS. A página pública e o painel podem viver no mesmo projeto, em rotas separadas (`/` para a página pública e `/painel` para o painel).
- **Banco e autenticação:** Supabase (Postgres com login pronto e regras de acesso por linha). Só o Tarsis faz login na fase 1.
- **Hospedagem:** Vercel ou similar, com domínio no nome do Tarsis.
- **Alternativa mais simples**, se o desenvolvedor ainda estiver começando: uma ferramenta no-code ou low-code para o painel. Apresente as trocas: mais rápido no início, menos controle e possível custo mensal maior.

Preços, limites de plano gratuito e versões mudam. Sempre diga que precisam ser conferidos na hora.

## Modelo de dados inicial

- `professores`: nome, modelo de ganho (100%, divisão percentual ou aluguel), percentual, WhatsApp.
- `modalidades`: nome, tipo (individual ou turma), vagas (para turmas), professor responsável.
- `alunos`: nome, WhatsApp, responsável (se menor de idade), status (interessado, experimental, ativo, inativo).
- `matriculas`: aluno, modalidade, professor, dia da semana, horário, duração, valor mensal, início, fim.
- `aulas`: ocorrência de uma aula numa data (gerada a partir da matrícula, ou avulsa, experimental ou reposição), local (studio ou externo), endereço se externo.
- `presencas`: aula, aluno, status (presente, falta, falta avisada), data e hora do aviso. A regra das 24h decide se gera direito a reposição.
- `pre_reservas`: dados da triagem, horário pedido, status (pendente, aprovada, recusada, expirada), criada em.
- `locacoes_sala`: professor locatário, data, início, fim, valor.
- `pagamentos`: aluno ou locatário, competência (mês), valor previsto, valor pago, data, forma.

Repasses não precisam de tabela própria na fase 2: são calculados a partir dos pagamentos e do modelo de ganho do professor.

Conflito de horário: uma aula, aula externa (somando o tempo de deslocamento) ou locação não pode se sobrepor a outra do mesmo professor, nem duas atividades podem ocupar a sala ao mesmo tempo.

## Padrões de front-end

- Mobile first: desenhe para 375px de largura e depois amplie.
- Componentes pequenos e com um propósito só. Nomes em português para o domínio (`CartaoAula`, `ListaPreReservas`) são aceitáveis e ajudam o aprendizado.
- Todo componente que busca dados trata os estados de carregando, vazio e erro.
- Formulários: rótulo visível em todo campo, validação com mensagem clara ao lado do campo, botão principal único.
- Acessibilidade: contraste mínimo de 4.5:1, área de toque de pelo menos 44px, navegação por teclado no painel.
- Datas e horários no fuso de Brasília e no formato brasileiro.

## Segurança e LGPD

- A página pública nunca expõe nomes ou contatos de alunos, só disponibilidade.
- Colete só o necessário: nome e WhatsApp na pré-reserva. Para menores, contato do responsável.
- Aviso de privacidade curto na página pública.
- Regras de acesso no banco: só usuários autenticados leem dados de alunos.

## Formato de ADR

```
ADR-001: [título]
Contexto: [o problema e as opções]
Decisão: [o que foi escolhido]
Consequências: [o que fica mais fácil, o que fica mais difícil]
```

## Decisões registradas

ADR-001: Código com apoio de IA, Next.js + Supabase + Vercel
Contexto: o desenvolvedor sabe o básico de front-end e quer o projeto publicado na Vercel, com o código sob controle dele. Foi considerado no-code (Bubble, Glide, AppSheet), descartado porque prende à plataforma e não publica na Vercel.
Decisão: seguir a stack sugerida acima (Next.js com TypeScript e Tailwind, Supabase para banco e login, Vercel para hospedagem, código no GitHub). A IA (a squad, v0, Claude Code ou similares) acelera a escrita do código, mas o desenvolvedor lê, entende e aprova cada parte. Ordem de construção: banco de dados, depois a agenda do painel (dor principal), depois a página pública, que lê a mesma disponibilidade.
Consequências: código e dados pertencem ao projeto, sem dependência de plataforma no-code, e o desenvolvedor ganha experiência valorizada. Em troca, precisa aprender o básico de React, GitHub, variáveis de ambiente e publicação. Atenção: conferir se o plano gratuito da Vercel permite uso comercial e as regras de pausa do plano gratuito do Supabase antes de colocar em produção.
