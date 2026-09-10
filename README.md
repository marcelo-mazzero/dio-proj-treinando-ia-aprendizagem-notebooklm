# Treinando uma IA de Aprendizagem: Explore o Poder do NotebookLM

> **Projeto prático desenvolvido por Marcelo Mazzero para o [Bootcamp da DIO & Bradesco sobre GenAI, Dados e Cibersegurança](https://www.dio.me/bootcamp/bradesco-dados-ciberseguranca-genai)**

> **Tema:** O Método SuperCarteira da Indê Investimentos
> > Escolhi esse tema porque ele une dois interesses meus: educação financeira e a curiosidade de testar até onde uma IA como o NotebookLM consegue organizar um conteúdo técnico e cheio de jargão em algo que eu realmente use depois.

---


## 1. Contexto e Objetivos

### 1.1 Contexto do Problema
O investidor pessoa física comum é constantemente bombardeado por ruídos de curto prazo: previsões macroeconômicas sensacionalistas, dicas quentes de ações (*stock picking* especulativo) e recomendações de produtos de prateleira enviesados por conflitos de interesse bancários. Sob a pressão da volatilidade e do medo, o cérebro biológico entra no circuito ancestral de "luta ou fuga", levando a decisões impulsivas — comprar no topo da euforia e vender no fundo do pânico.

Este projeto utiliza o **Google NotebookLM** como uma ferramenta de **aprendizagem ativa de alta fidelidade**.

O objetivo foi construir um assistente de estudos capaz de sintetizar, analisar e operacionalizar o **Método SuperCarteira**, estruturado pela Indê Investimentos e apresentado durante a imersão "A Independência" (agosto/2026) pela fundadora desta casa de análise, analista e planejadora financeira **Luciana Seabra**, e inspirado em três pilares acadêmicos fundamentais:
1. **O Modelo Yale de Alocação de Ativos** de *David Swensen*
2. **A Teoria da Antifragilidade** de *Nassim Nicholas Taleb*
3. **As Finanças Comportamentais e a Neuroeconomia** de *Daniel Kahneman, Amos Tversky e Shawn Achor*

### 1.2 Objetivos de Estudo
* **Objetivo:** Estruturar a matriz de caixas temporais (Segurança, Estabilidade, Diversificação, Valorização, Antifragilidade, Satélite e Previdência) com seus respectivos horizontes de resgate e classes de fundos utilizando IA e Engenharia de Prompts para investigar a fundo a capacidade de recuperação de contexto do NotebookLM, documentando o processo de iteração, falhas de recuperação inicial (*troubleshootings*) e desenvolvimento de um kit reutilizável de comandos de alto nível.

---


## 2. Estrutura do Repositório

O projeto foi organizado de forma modular para facilitar a navegação técnica e a reprodutibilidade:

```text
├── README.md                      # Visão geral do projeto
├── fontes.md                      # Detalhamento das fontes
├── prompts.md                     # Registro de testes, prompts iterativos e troubleshooting
└── guia-de-estudo.md              # Síntese do projeto com glossário e prompts reutilizáveis
```

---


## 3. Como Reproduzir no NotebookLM

1. **Acesse a plataforma:** Faça login no [Google NotebookLM](https://notebooklm.google.com/)
2. **Crie um novo caderno:** Nomeie como `Estudos do Método SuperCarteira`
3. **Faça o upload das fontes:** Insira os materiais listados em [fontes.md](./fontes.md)
4. **Execute as prompts:** Utilize os prompts disponíveis em [prompts.md](./prompts.md)
5. **Aplique o passo a passo:** Consulte o [guia-de-estudo.md](./guia-de-estudo.md)

---


## 4. Aviso

Este repositório é apenas para fins de estudo pessoal. Percentuais de alocação, rentabilidades históricas e recomendações de produtos citados não constituem recomendação de investimento e devem ser verificados antes de qualquer decisão financeira.

---


Desenvolvido por **Marcelo Mazzero** em setembro/2026.
