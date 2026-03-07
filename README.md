# DESAFIO-QA-BEEDOO-2026

Repositório destinado à entrega do desafio técnico para a vaga de Analista de Qualidade de Software Júnior.

---

## 1. Análise Inicial da Aplicação

### Objetivo
A aplicação consiste em um sistema de gerenciamento de cursos (CRUD - Create, Read, Update, Delete), permitindo o cadastro de novos cursos com especificações dinâmicas e a visualização destes em um dashboard interativo.

### Fluxos Principais
* **Cadastro:** Entrada de dados com campos condicionais baseados na modalidade do curso (Presencial vs. Online).
* **Listagem (Dashboard):** Exibição dos cursos cadastrados através de cards informativos.
* **Exclusão:** Funcionalidade de remoção de registros da base de dados/interface.

### Pontos Críticos Identificados
1.  **Regra de Negócio Condicional:** A alternância entre os campos "Endereço" e "Link de Inscrição" é um ponto de alta probabilidade de erro de UI/UX.
2.  **Integridade das Datas:** A lógica que impede uma data de término ser anterior à de início é vital para a consistência dos dados.
3.  **Persistência:** Garantir que os dados não sejam perdidos após um refresh (F5).
4.  **Feedback ao Usuário:** O sistema precisa comunicar claramente se uma ação (cadastro ou exclusão) foi concluída com sucesso.

---

## 2. Decisões de Teste e Raciocínio

Para a criação dos cenários, utilizei a técnica de **Particionamento de Equivalência** e **Análise de Valor Limite**.

* **Cenários Positivos:** Focados em garantir que o "Caminho Feliz" (Happy Path) atenda aos requisitos básicos de funcionamento.
* **Cenários Negativos:** Estruturados para testar a resiliência do sistema contra entradas inválidas (datas impossíveis, campos vazios e formatos de URL incorretos).
* **Testes de Interface (GUI):** Verificação da visibilidade dinâmica dos campos conforme a modalidade escolhida.

---

## 3. Links do Desafio

* **Planilha de Casos de Teste (Google Sheets):** [INSIRA O SEU LINK AQUI]
* **Evidências de Execução (Prints/Vídeos):** [INSIRA O LINK DA PASTA NO DRIVE AQUI]

---

## 4. Relatórios de Bug Encontrados

### [BUG-001] Falha Funcional no Botão de Exclusão
* **Severidade:** Crítica
* **Descrição:** Ao clicar no botão "Excluir Curso" em um card no dashboard, o sistema não executa nenhuma ação e o curso permanece listado.
* **Passos para reproduzir:**
    1. Cadastrar um curso qualquer.
    2. Localizar o curso no Dashboard.
    3. Clicar no botão "Excluir Curso".
* **Resultado Atual:** O card permanece na tela e não há erro visível no console.
* **Resultado Esperado:** O curso deve ser removido da listagem e da memória da aplicação.

---

## 5. Uso de Inteligência Artificial

Neste desafio, utilizei a IA como uma ferramenta de **apoio consultivo**. 
* **Como utilizei:** Auxílio na estruturação da documentação e brainstorming de cenários de teste negativos.
* **Análise Crítica:** Refinei as sugestões da IA para garantir que os cenários estivessem alinhados exatamente com os campos visíveis na aplicação analisada, descartando sugestões genéricas e focando na lógica condicional de "Endereço/Link" que identifiquei manualmente.
