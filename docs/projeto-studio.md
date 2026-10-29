# Projeto: Sistema do Studio do Tarsis

## Índice
1. Contexto e dor
2. As duas ferramentas
3. Regras de negócio confirmadas
4. Fluxos
5. Fases
6. Pendências
7. Projeto de referência: barbearia

## 1. Contexto e dor

Studio de música do Tarsis (fundador). Cerca de 8 alunos e 3 professores. Modalidades: canto, teclado, violão, guitarra, baixo, coral e grupo de louvor. O studio também é usado por um professor que aluga a sala.

Dores confirmadas pelo próprio Tarsis: ele se perde na agenda (aulas próprias, aulas dos outros professores, aulas externas e sala alugada) e perde tempo "entrevistando" pelo WhatsApp quem encontra o número dele no Google.

## 2. As duas ferramentas

**Página pública** (o vendedor e recepcionista). Acessada pelo link "Site" no Perfil da Empresa no Google. Funcionamento: triagem com toques (instrumento, nível, objetivo, para quem é a aula), agenda do professor daquele instrumento mostrando só "livre" ou "indisponível" (nunca nomes) e vagas restantes nas turmas, pré-reserva de aula experimental com nome e WhatsApp, tela de confirmação e botão para o WhatsApp do Tarsis com mensagem pronta (link wa.me com texto preenchido). Preço visível: "a partir de R$ 62,50 por aula no pacote mensal de 4 aulas".

**Painel** (o gerente). Tela "Hoje" (aulas do dia, pré-reservas para aprovar, pagamentos atrasados), agenda semanal de todos os professores com cores por tipo (aula no studio, aula externa, sala alugada, experimental), horários fixos recorrentes, aviso de conflito, alunos com presença em um toque, financeiro com previsto e recebido, pago em um clique e repasses automáticos.

Frase que resume: a página traz o aluno, o painel cuida dele.

## 3. Regras de negócio confirmadas

- Pacote: 4 aulas por R$ 250 por mês.
- Lucas dá aulas de guitarra, baixo e violão. O valor das aulas dele é dividido meio a meio: 50% para o Tarsis, 50% para o Lucas.
- Tarsis recebe 100% das próprias aulas. Modalidades dele, a confirmar: canto, teclado, coral e grupo de louvor.
- Mike paga aluguel pela sala. Valor ainda não definido. O painel deve registrar as horas de uso para ajudar a definir o valor.
- Reposição: só tem direito a reposição a falta avisada com pelo menos 24 horas de antecedência. Falta sem esse aviso não gera reposição.
- Pré-reserva de experimental fica pendente até o Tarsis aprovar no painel. Sem resposta em 24 horas, expira e libera o horário.
- Coral e grupo de louvor são turmas com limite de vagas.

## 4. Fluxos

Captação: aluno pesquisa no Google → clica em "Site" → triagem → escolhe horário do professor certo → pré-reserva e WhatsApp com mensagem pronta → Tarsis aprova no painel (ou expira em 24h) → aula experimental → fechou o pacote? Sim: vira aluno com horário fixo e professor. Não: fica no funil como contato.

Rotina: horário fixo se repete toda semana → aula acontece (no studio ou externa) → presença com um toque (falta avisada com 24h gera reposição) → pagamento marcado (previsto contra recebido) → fechamento do mês com repasse do Lucas e aluguel do Mike.

## 5. Fases

- Fase 1: página pública completa e painel com agenda, pré-reservas, alunos e presença.
- Fase 2: financeiro com repasses, aluguel da sala e turmas com vagas.
- Fase 3: funil de alunos (interessados, experimental, matriculados), lembretes automáticos e programa de indicação.
- Fora por enquanto: pagamento online, app para baixar, acesso próprio dos outros professores.

Sucesso em 30 dias: toda a agenda no sistema, zero conflito de horário, menos tempo do Tarsis no WhatsApp, primeiras pré-reservas chegando pela página.

## 6. Pendências

- Horários e agendas de cada professor: o Tarsis vai sentar com o desenvolvedor para organizar.
- Detalhes do Mike: valor do aluguel e se ele aparece na página pública ou só no painel.
- Confirmar as modalidades que o próprio Tarsis dá.
- Aulas externas: onde acontecem e tempo de deslocamento.
- Logo e fotos do studio.
- Nível de React do desenvolvedor (ele sabe o básico de front-end; confirmar se já usou React).

## 7. Projeto de referência: barbearia

Projeto anterior do mesmo desenvolvedor: fila virtual com pagamento antecipado para uma barbearia de bairro que atende por ordem de chegada (3 barbeiros). Dor: corte fiado. Ideias que se reaproveitam no studio: estrutura cliente-profissional-serviço, painel simples do profissional, relatório do dia e do mês por profissional e comissão automática (no studio, vira o repasse do Lucas). Diferença central: a barbearia gira em torno de fila em tempo real; o studio gira em torno de agenda recorrente. Uma base comum (cadastro, serviços com valor, pagamentos, relatórios) pode servir aos dois projetos.
