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
| # | História (Como… quero… para…) | INVEST: o que falha |
|---|---|---|

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
