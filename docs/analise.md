# Documento de Análise — Prato Cheio

*Trabalho 1 · máximo 4 páginas · entrega na Aula 5*

## Problema central

## Incertezas

## Stakeholders
| Stakeholder | Interesse | Influência | O que espera | O que muda na iteração 1 |
|---|---|---|---|---|
| Doadores | Médio | Alta | Doar sem burocracia e com retirada rápida, não quer perder tempo cadastrando produto. | São os primeiros que a gente precisa ouvir sobre o que é díficl de preencher. É por causa deles que o cadastro ficou só com tipo, quantidade e validade, nada mais. |
| ONGs | Alto | Médio | Saber com antecedência o que vai chegar, pra conseguir planejar as refeições. | São elas que vão confirmar se só "tipo + quantidade + validade" já é suficiente pra decidir se aceitam, sem precisar ligar perguntando mais coisa. |
| Entregadores Voluntários | Médio | Baixo | Um sistema simples de usar no celular. | Ficam de fora por enquanto — a história zero vai só até a ONG aceitar a doação, não chega na parte da coleta. |
| Marta | Alto | Alto | Crescer e mostrar resultado pra conseguir apoio. | É ela quem decide se o caminho mínimo (publicar → ver → aceitar) é piloto suficiente, e o que fica pra depois. |
| Vigilância sanitária | Baixo | Alta | Um registro mínimo de cada doação. | A gente nem conversa com ela ainda, mas os três campos que ela exige já entram sem discussão, porque isso é regra, não é coisa que dá para negociar. |
| Quem recebe a comida | Alto | Nulo | Receber as doações com frequência. | Eles não entram em nenhuma conversa nossa nessa iteração, quem fala por eles é a ONG. |

## Objetivos de impacto
1. **Diminuir a quantidade de comida boa que é jogada fora.**
- **Como vamos medir:** % das doações publicadas que vencem sem ninguém aceitar por semana no bairro.
- **De onde parte esse número:** No momento ainda não temos nenhum dado para calcular porque isso nunca foi medido. Vamos começar a medir já na primeira semana.
- **Pra onde queremos ir:** Esse número tem que cair, semana após semana, comparado com as semanas anteriores.
2. **Aumentar quantas refeições chegam pra quem precisa.**
- **Como vamos medir:** Quantidade de doações aceitas e realmente coletadas por semana.
- **De onde parte:** Também não sabemos hoje, o caso nem diz quantas ONGs vão entrar. A contagem começa no primeiro dia.
- **Pra onde queremos ir:** esse número deve crescer, semana a semana.
3. **Diminuir o tempo entre a comida ficar disponível e ser coletada.**
- **Como vamos medir:** Tempo médio, em horas, entre a doação ser publicada e ser aceita por alguma ONG.
- **De onde parte:** a Marta acha que esse é o gargalo, mas ninguém mediu isso ainda. Então iremos analisar os dados da primeira semana e se possível colocar as doações para serem aceitas apenas nos bairros publicados.
- **Pra onde queremos ir:** Esse tempo médio precisa cair ao longo das entregas.

## Regras de negócio
**Regra 1 – identificação do doador**
- **Origem:** Derivada (a vigilância não fala "nome e telefone", mas sem isso não dá pra rastrear).
- **Enunciado:** Toda doação publicada precisa ter nome completo e telefone de contato do doador.
- **Como verificar:** Tentar cadastrar sem esses dados, o sistema barra e mostra a mensagem "Nome e telefone do doador são obrigatórios".
 
**Regra 2 – Tipo de alimento com lista fechada**
- **Origem:** Inventada (a gente padronizou pra facilitar busca).
- **Enunciado:** O campo tipo de alimento é obrigatório e tem que escolher de uma lista: Refeição pronta, Padaria, Hortifruti, Laticínios, etc. Não pode escrever texto livre.
- **Como verificar:** Abrir o formulário de doação e ver que o campo é um dropdown com essas opções. Enviar com "tipo" vazio é recusado.

**Regra 3 – Prazo pra ONG retirar**
- **Origem:** ausente (o caso não diz o que acontece se a ONG aceita e não busca).
- **Enunciado:** Se a ONG aceitar e não confirmar a retirada em 2 horas, a doação volta pra 'disponível' e a ONG perde a reserva.
- **Como verificar:** Simular aceitação, não confirmar retirada e checar que depois de 120 minutos a doação fica livre de novo.
- **Quem decide:** Marta e as ONGs do piloto, até a data de revisão do piloto. Enquanto isso, vale a regra que foi inventada.

## Conflitos de prioridade
**Conflito escolhido:** A vigilância precisa rastrear quem está doando; o doador quer só fazer a boa ação rápido, sem ter que dar seus dados.
 
**Fala de cada lado:**
 
- **Vigilância/Sistema:** "Eu preciso do nome e do telefone de quem doou. Se der algum problema com a comida, eu tenho que saber o nome do doador."
 
- **Doador:** "Poxa, eu só quero entregar a comida e ajudar. Não quero ficar preenchendo cadastro nem dar meu número pessoal."
 
- **Qual é a briga de verdade:** É a segurança brigando com a praticidade. Para garantir que a comida não vai fazer mal a ninguém, a gente precisa pedir esses dados. O problema é que criar essa barreira de cadastro pode dar preguiça ou desanimar quem só queria fazer uma doação rápida e sem compromisso.
 
- **O que cada lado perde:** Se o sistema aceitar doação anônima, a gente perde o controle e fica correndo o risco de passar comida pra frente sem saber de onde veio. Por outro lado, se a gente exigir os dados, o doador perde a praticidade, e a gente corre o risco de ele achar burocrático demais e desistir de doar.
 
- **Qual é o critério pra decidir:** Como a base dessa regra vem da necessidade da vigilância sanitária, não dá para negociar. Rastrear a comida é o mais importante. É melhor a gente correr o risco de perder um ou outro doador por causa do cadastro do que deixar circular comida de origem desconhecida que pode intoxicar alguém.
 
- **Qual saída a gente usou:** A segurança ganhou sem conversa. A gente simplesmente travou a doação anônima. Se a pessoa tentar publicar sem dar os dados, o sistema não deixa avançar e mostra a mensagem na tela: "Nome e telefone do doador são obrigatórios". Assim a gente garante que nenhuma comida entre no aplicativo sem ter o responsável amarrado a ela.

## Histórias de usuário
| # | História (Como… quero… para…) | INVEST: o que falha | Ação corretiva |
|---|---|---|---|
| ★ | Como ONG receptora, quero aceitar uma doação disponível e vê-la sumir da lista para as demais, para que nenhum voluntário seja mandado atrás de uma doação que outra ONG já garantiu. | Independente: depende de existir doação publicada e listada antes; é o alicerce de tudo, não dá pra reordenar. | Mantém-se assim mesmo falhando: é a exceção prevista pelo INVEST, o valor desta história é para o time (monta o caminho de entrega ponta a ponta e produz a medição de tempo publicação→aceite que a Aula 2 mostrou não existir), não para um usuário específico. Não caçamos independência artificial aqui. |
| 1 | Como doador (restaurante, padaria ou mercado), quero publicar uma doação em menos de 30 segundos, para não desistir no meio do cadastro e a comida sair da cozinha antes de estragar. | Negociável: a primeira redação já vinha com "formulário com tipo em lista suspensa, quantidade em campo numérico, validade em seletor de data e botão azul 'Publicar'". | Tiramos o desenho de tela de dentro da história e movemos dropdown/datepicker/cor do botão para os critérios de aceite e o protótipo; a história ficou só com o comportamento e o tempo-limite observável. |
| 2 | Como vigilância sanitária, quero que toda doação publicada tenha nome completo e telefone do doador registrados, para conseguir rastrear a origem se algum alimento fizer mal a alguém. | Testável: a primeira versão dizia só "quero garantir a rastreabilidade das doações", sem nenhuma condição observável. | Reescrevemos como Dado/Quando/Então usando a Regra 1 já registrada neste documento: dado que o doador tenta publicar sem nome/telefone, quando envia o formulário, então o sistema recusa e mostra "Nome e telefone do doador são obrigatórios". |
| 3 | Como Marta, quero ver o tempo entre a publicação e o aceite de cada doação, para confirmar se a coleta é mesmo o gargalo antes de mudar qualquer processo. | Pequena: a primeira versão era "um relatório completo de doações, aceites e voluntários, para gerenciar tudo", com "e" no meio e cara de módulo inteiro. | Fatiamos e deixamos só a métrica que valida (ou derruba) a hipótese da Marta nesta iteração, tempo entre publicação e aceite. Relatório de voluntários e gestão completa viram backlog da iteração 2, não são descartados. |
| 4 | Como voluntário, quero confirmar que retirei uma doação, para a Marta saber quanto tempo a coleta realmente leva e eu não continuar "responsável" por uma doação que já não está comigo. | Valiosa: a primeira versão era "como voluntário, quero confirmar a coleta, para que o sistema registre a coleta": valor do sistema, não de alguém. | Achamos quem sente falta de verdade (a Marta, que precisa da medição; e o próprio voluntário, que não quer ficar de posse "fantasma" de uma doação já entregue) e reescrevemos o "para" apontando pra eles. |
| 5 | *(fatia 1/3 do gigante "Como ONG, quero encontrar e aceitar a doação certa para mim")* Como ONG receptora, quero ver a lista completa de doações disponíveis (ordem de publicação) com tipo, quantidade e validade, e aceitar com um clique só, para decidir com o mínimo de informação, sem depender de nenhum filtro. | Independente: pelo mesmo motivo da história zero. | Mantemos mesmo assim: é a "linha dos mínimos" do método hambúrguer e converge com o núcleo funcional da história zero (★) evidência de que a primeira fatia se escolhe por risco, não por valor. É a base sobre a qual as fatias 2 e 3 se apoiam. |
| 6 | *(fatia 2/3 do gigante)* Como ONG receptora, quero filtrar a lista de doações por tipo de alimento, para não perder tempo lendo itens que a minha organização não recebe. | Estimável: não sabemos hoje se a lista fechada de tipos (Regra 2) cobre os casos reais das ONGs do piloto. | Spike de 1h conversando com 2 ONGs do piloto para confirmar se a lista fechada de tipos já é suficiente, antes de estimar o filtro. |
| 7 | *(fatia 3/3 do gigante)* Como ONG receptora, quero ver um resumo da doação (tipo, quantidade, validade e nome do doador) antes de confirmar o aceite, para não travar por engano uma doação que não vou conseguir buscar. | Negociável: a primeira versão já vinha com "uma modal de confirmação com dois botões, 'Confirmar' verde e 'Cancelar' cinza". | Tiramos a modal e as cores da história e deixamos como critério de aceite; a história descreve só o comportamento (mostrar o resumo antes de travar a reserva). |

**★ História zero — por que ela e o que ficou fora**

*Por que ela:* a regra de negócio central do caso é que, depois que uma ONG aceita uma doação, ela some para as outras, sem essa regra funcionando de ponta a ponta (publicar → listar → aceitar com trava de concorrência), nenhuma das outras histórias tem base para se apoiar, e a Aula 2 mostrou que hoje não existe nenhuma medição do tempo entre publicação e aceite; a história zero é a única fatia que produz essa linha de base (por isso registra os dois instantes — publicação e aceite —, mesmo que isso signifique acrescentar uma coluna nova no schema além do que os cinco `it.todo` já cobrem).

*O que ficou FORA da fatia, e por quê (risco ou medição, nunca "é difícil"):*
- **Autenticação de doador e de ONG**: não exercita a regra central (aceitar → sair da lista) nem produz nenhuma medição; é atrito adicionado sem reduzir risco.
- **Filtro por proximidade**: o caso só registra que ONG perto do doador "leva vantagem" como fato observado, não como regra decidida (Aula 2); implementar o filtro hoje transformaria um fato em regra de prioridade sem dono definido.
- **Notificação em tempo real**: o orçamento do piloto é próximo de zero e não há canal definido; um canal de notificação sem esse custo validado é risco de estourar a restrição de negócio do caso.
- **Foto da doação**: não está em nenhum dos cinco `it.todo` nem na regra central; não reduz risco de concorrência nem produz medição, é luxo, não walking skeleton.
- **Expiração automática da reserva (Regra 3 — prazo de 120 minutos)**: a Regra 3 está classificada neste documento como "origem: ausente"; Marta e as ONGs do piloto ainda precisam ratificá-la. Implementar antes disso seria decidir uma regra de negócio sem dono.

## Critérios de aceite
**História X** — Dado … Quando … Então …

## Riscos
| Risco | Probabilidade | Impacto | Mitigação |
|---|---|---|---|

## Hipótese e experimento

## Decisão de análise
- **Problema:**
- **Alternativas:**
- **Decisão e justificativa:**
- **Riscos e limitações:**

## Uso de IA
O que geramos com IA, o que verificamos e o que alteramos.
