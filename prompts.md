# Engenharia de Prompts e Troubleshooting

Este documento registra os prompts executados dentro do NotebookLM e a análise das respostas geradas pela IA.

---

## Experimento 1

### Objetivo
Extrair com exatidão a matriz de alocação de ativos do Método SuperCarteira, correlacionando o nome de cada caixa, seu horizonte temporal mínimo, ativos permitidos e classes de risco.

### Prompt V1
```text
Como são divididas as caixas de investimento na SuperCarteira?
```

* **Resposta Obtida:** A IA forneceu um resumo genérico dizendo que a carteira era composta por renda fixa para segurança, fundos multimercados para diversificação e ações para ganho de capital. Não mencionou a caixa de "Antifragilidade", ignorou completamente os prazos recomendados (6 meses, 3 anos, 5 anos) e confundiu a Reserva de Emergência com a Caixa de Estabilidade.
* **Troubleshooting:**
  * *Ambiguidade semântica:* A palavra "caixas" é comum no mercado financeiro. Sem vincular explicitamente à Fonte 1, o modelo completou lacunas com o repertório prévio da internet.
  * *Ausência de esquema relacional:* O modelo não foi orientado a estruturar os dados em tabela comparativa, gerando texto corrido prolixo.

### Prompt V2
```text
Com base estritamente na Fonte 1, construa uma tabela comparativa exaustiva de todas as caixas de investimento do método.

A tabela deve conter exatamente as seguintes colunas:
1. Nome da Caixa
2. Prazo Mínimo Recomendado
3. Instrumentos e Classes de Ativos Permitidos
4. Subcategorias Internas (ex: Baunilha / Pimentinha)
5. Percentual na Alocação Estrutural (para quem possui recursos para todas as caixas, excluindo a reserva de emergência)

Se houver classes opcionais ou satélites, especifique as regras e limites percentuais máximos logo abaixo da tabela.
```

* **Resposta Obtida:**
  O modelo gerou com precisão cirúrgica a matriz completa:
  * **Segurança:** Prazo Imediato (0) | Fundo taxa zero de Tesouro Selic | Reserva de emergência fora do percentual.
  * **Estabilidade:** Prazo >= 6 meses | Crédito privado pós-fixado CDI | Subdivisão em *Baunilha* (baixo risco) e *Pimentinha* (alta taxa) | **40,0%**.
  * **Diversificação:** Prazo >= 3 anos | Multimercados Macro, Ex-tesoureiros, Global, Debêntures de Infraestrutura e Agro | **30,0%**.
  * **Valorização:** Prazo >= 5 anos | Ações BR (Qualidade, Fora do Radar), ETFs Globais, Private Equity | **22,5%**.
  * **Antifragilidade:** Prazo Permanente | Ouro e Dólar | **7,5%**.
  * **Satélite (Nota de rodapé):** Criptoativos | Prazo >= 10 anos | Opcional, com limite rígido de até **3%** da carteira.

---

## Experimento 2

### Objetivo
Avaliar se a IA compreende a visão não convencional da apresentadora sobre Previdência Privada, desconstruindo o mito de que "previdência é sempre um investimento ruim".

### Prompt V1
```text
A previdência privada é um investimento bom ou ruim de acordo com o material?
```

* **Resposta Obtida:** A IA entrou em contradição. Afirmou que a previdência possui altos custos de administração e taxas de carregamento, mas depois comentou que pode ser vantajosa para aposentadoria. Em momento algum explicou os 4 diferenciais tributários específicos citados na videoaula.
* **Troubleshooting:**
  * *Viés de treinamento geral:* O modelo priorizou os milhões de textos na internet que criticam a previdência tradicional de bancões, ofuscando a tese de "Previdência como Capa Mágica Tributária".

### Prompt V2
```text
Localize na Fonte 1 o trecho em que a Luciana Seabra aborda a pergunta: "Previdência privada não é ruim?". 

Explique em detalhes a resposta fornecida pela Luciana Seabra, abordando:
1. Por que ela define a previdência como uma "capa mágica" para os fundos de investimento?
2. Quais são os 4 benefícios fiscais e sucessórios explícitos listados no PDF?
3. Qual é a regra de alocação da Previdência em relação às caixas da SuperCarteira?

Restrinja sua resposta aos dados das fontes.
```

* **Resposta Obtida:**
  O NotebookLM recuperou com exatidão os fundamentos:
  1. **A Capa Mágica:** A previdência não é um ativo em si, mas um invólucro jurídico-tributário. Colocar um bom fundo dentro dessa estrutura transforma a eficiência do investimento.
  2. **Os 4 Benefícios Explícitos:**
     * *Dedução no IRPF:* Abate de até 12% da renda bruta tributável na declaração completa (PGBL);
     * *Alíquota mínima de 10%:* No regime regressivo após 10 anos de acumulação;
     * *Alíquota zero:* Possibilidade legal de tributação 0% se o usufrutuário for dependente sem renda tributável (ex: filhos menores);
     * *Planejamento sucessório:* Isenção de ITCMD (imposto sobre herança) na maioria dos estados e ausência de inventário;
     * *Ausência de Come-Cotas:* O reinvestimento integral sem antecipação semestral de IR acelera os juros compostos.
  3. **Regra de Alocação:** A carteira previdenciária deve replicar a mesmíssima distribuição estrutural da carteira líquida (Estabilidade, Diversificação, Valorização e Antifragilidade).

---

## Experimento 3

### Objetivo
Criar uma ponte epistemológica entre a psicologia da tomada de decisão e a regra prática de rebalanceamento de carteiras proposta pelo Modelo Yale.

### Prompt V1
```text
Qual a ligação entre Daniel Kahneman e David Swensen nos investimentos?
```

* **Resposta Obtida:** A resposta gerou duas biografias independentes: resumiu que Kahneman escreveu sobre finanças comportamentais e que Swensen geriu o fundo de Yale. Não articulou a relação de causa e efeito entre os dois conceitos dentro da tomada de decisão de um portfólio.
* **Troubleshooting:**
  * *Falta de persona e comando de causalidade:* O prompt perguntou "qual a ligação", o que permite ao modelo apenas justapor conceitos. Faltou instruir a IA a pensar nas consequências comportamentais do rebalanceamento mecânico.

### Prompt V2
```text
Assuma o papel de um Gestor de Portfólio especialista em Finanças Comportamentais.

Utilizando a Fonte 1, Fonte 2 e Fonte 3, estabeleça a relação de causalidade entre os seguintes pontos:
1. O conflito entre o "Cérebro Impulsivo" e o "Cérebro Pensador" sob a dor da aversão à perda de 2 para 1;
2. A afirmação de David Swensen: "O rebalanceamento é o suprassumo do comportamento racional";
3. A regra prática da SuperCarteira: "Se alguma fatia ficar acima da alocação estrutural, eu vendo; se ficar abaixo, eu compro".

Explique de que maneira a disciplina mecânica do rebalanceamento atua como uma 'prótese comportamental' que protege o investidor de seu próprio cérebro.
```

* **Resposta Obtida:**
  A síntese final gerada pelo assistente foi impecável:
  * **O Dilema Biológico:** Quando os mercados desabam, a neurobiologia processa perdas patrimoniais como perigo de morte real (tigre-dentes-de-sabre). Como perder R$ 10.000 dói duas vezes mais do que ganhar R$ 10.000 (aversão à perda de Kahneman), o *Cérebro Impulsivo* aperta o botão do pânico para cessar a dor, provocando a liquidação de ativos no fundo do poço.
  * **A Função de Swensen:** O rebalanceamento é o "suprassumo da racionalidade" exatamente porque é **antinatural e contracíclico**. Ele exige retirar dinheiro dos ativos que estão em alta (amados pela manada) para aportar nos ativos em queda (rejeitados pelo mercado).
  * **A Solução Sistêmica:** A regra mecânica ("subiu além do alvo = vendo; caiu abaixo = compro") neutraliza o arbítrio emocional. O investidor não precisa "adivinhar o futuro" nem ter sangue-frio heroico: ele apenas executa uma regra matemática pré-estabelecida pelo Cérebro Pensador em momentos de calma.

---

## Experimento 4

### Objetivo
Garantir a fidedignidade da transcrição de dados quantitativos de desempenho de fundos recomendados em uma década (01/01/2016 a 31/12/2025).

### Prompt V1
```text
Quanto renderam os fundos recomendados na Fonte 1?
```

* **Resposta Obtida:** A IA disse que "os fundos recomendados renderam centenas de por cento e bateram a bolsa", sem apresentar a tabela comparativa e errando o período de corte da lâmina.

### Prompt V2
```text
Consulte a Fonte 1 ("Retorno de fundos recomendados em uma década - 01/01/2016 a 31/12/2025").

Extraia a tabela exata com todos os investimentos listados e seus respectivos retornos percentuais acumulados. Inclua a fonte original dos dados citada no PDF e explique qual é o argumento central da Luciana Seabra ao apresentar esses números diante da objeção comum de que 'fundos de investimento não valem a pena'.
```

* **Resposta Obtida:**
  * **Tabela Extraída:**
    * *FIC Ações (destaque 1):* 797,73%
    * *Multimercado (destaque 1):* 477,97%
    * *FIC Ações (destaque 2):* 461,25%
    * *Multimercado (destaque 2):* 400,34%
    * *FIC Ações (destaque 3):* 341,56%
    * *Ibovespa (média da Bolsa):* 271,69%
    * *IMA-B (títulos de inflação):* 180,21%
    * *CDI (renda fixa conservadora):* 144,18%
    * *Dólar:* 40,91%
  * **Fonte dos dados:** Quantum Axis com base na CVM.
  * **Argumento Central:** A média dos fundos realmente pode ser medíocre devido a produtos de baixa qualidade distribuídos por grandes bancos; no entanto, uma curadoria independente e criteriosa focada nos melhores gestores do país é perfeitamente capaz de entregar expressivo alfa e bater todos os índices de referência no longo prazo.

---

## Conclusões dos Prompts Utilizados
1. **Contexto delimitado (*Grounding*):** O NotebookLM atinge seu ápice de precisão quando o comando cita explicitamente a fonte, o autor e exige tabelas estruturadas.
2. **Combate a vieses da web:** Temas controversos (como Previdência Privada e Fundos de Investimento) exigem perguntas que peçam a tese do autor ("Por que a autora defende...") em vez de perguntas abertas ("Previdência é boa?").
3. **Poder de síntese conceitual:** A ferramenta se sobressai ao cruzar conceitos de fontes diferentes (Swensen + Kahneman + Taleb) desde que seja fornecido um mapa claro de relacionamento de causa e efeito.

---


Desenvolvido por **Marcelo Mazzero** em setembro/2026.
