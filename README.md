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
1.  **Cadastro e exclusão:** Devem estar funcionando perfeitamente pois são os fluxos principais do sistema.
2.  **Integridade das Datas:** A lógica que impede uma data de término ser anterior à de início é vital para a consistência dos dados.
   
---

## 2. Decisões de Teste e Raciocínio

Para a criação dos cenários, utilizei a técnica de **Particionamento de Equivalência** e **Análise de Valor Limite**.

* **Cenários Positivos:** Focados em garantir que o "Caminho Feliz" atenda aos requisitos básicos de funcionamento.
* **Cenários Negativos:** Estruturados para testar a resiliência do sistema contra entradas inválidas (datas impossíveis, campos vazios e formatos de URL incorretos).
* **Testes de Interface (GUI):** Verificação da visibilidade dinâmica dos campos conforme a modalidade escolhida.

---

## 3. Links do Desafio
* **Planilha de Casos de Teste (Google Sheets):** https://docs.google.com/spreadsheets/d/1ow77hsKEvhophui2LcDQf2oLZqpzlv77L3yRWAhznxQ/edit?usp=sharing
* **Evidências de Execução (Prints/Vídeos):** https://drive.google.com/drive/folders/1F-EgICU_xNn88I6dXQbdV-VPIV-hYGp-?usp=sharing

---

## 4. Relatórios de Bug Encontrados

### [BUG-001] Falha Funcional no Botão de Exclusão (CT-12)
* **Severidade:** Crítica
* **Descrição:** Ao clicar no botão "Excluir Curso" em um card no dashboard, o sistema não executa nenhuma ação e o curso permanece listado.
* **Passos para reproduzir:**
    1. Cadastrar um curso qualquer.
    2. Localizar o curso no Dashboard.
    3. Clicar no botão "Excluir Curso".
* **Resultado Atual:** O card permanece na tela e não há alteração na interface.
* **Resultado Esperado:** O curso deve ser removido da listagem imediatamente após a confirmação.

### [BUG-002] Ausência de Validação em Campos Obrigatórios (CT-03)
* **Severidade:** Alta
* **Descrição:** O sistema permite o envio do formulário de cadastro sem que nenhum campo tenha sido preenchido.
* **Passos para reproduzir:**
    1. Acessar a tela de cadastro.
    2. Clicar no botão para **cadastrar o curso** com todos os campos vazios.
* **Resultado Atual:** Um card vazio ou incompleto é gerado e exibido no dashboard.
* **Resultado Esperado:** O sistema deve exibir alertas de "Campo obrigatório" e impedir a criação do registro.

### [BUG-003] Falha na Lógica de Cronologia de Datas (CT-07)
* **Severidade:** Média
* **Descrição:** O sistema permite o cadastro de cursos onde a "Data de Fim" é configurada para um dia anterior à "Data de Início".
* **Passos para reproduzir:**
    1. No formulário de cadastro, inserir uma "Data de Início" futura (ex: 10/12/2026).
    2. Inserir uma "Data de Fim" passada (ex: 01/12/2026).
    3. Clicar para **cadastrar o curso**.
* **Resultado Atual:** O curso é cadastrado com sucesso apresentando datas logicamente impossíveis.
* **Resultado Esperado:** O sistema deve validar o período e exibir uma mensagem de erro impeditiva.

### [BUG-004] Falha de Limite de Caracteres - Nome e Descrição (CT-04 e CT-05)
* **Severidade:** Baixa (Interface)
* **Descrição:** Os campos de Nome e Descrição não possuem trava de caracteres, permitindo que textos muito longos quebrem a estrutura visual do card.
* **Passos para reproduzir:**
    1. Preencher o campo Nome com mais de 100 caracteres.
    2. **Cadastrar o curso** e visualizar o dashboard.
* **Resultado Atual:** O texto transborda os limites visuais do cartão, prejudicando a legibilidade.
* **Resultado Esperado:** O sistema deve limitar a entrada de caracteres no formulário para preservar o layout.

### [BUG-005] Aceitação de Valores Inválidos no Campo de Vagas (CT-09)
* **Severidade:** Média
* **Descrição:** O campo destinado ao número de vagas aceita números negativos, o que não condiz com a regra de negócio.
* **Passos para reproduzir:**
    1. No campo "Número de Vagas", digitar um valor negativo (ex: -10).
    2. Clicar para **cadastrar o curso**.
* **Resultado Atual:** O sistema aceita o valor e o exibe negativamente no dashboard.
* **Resultado Esperado:** O campo deve validar a entrada e permitir apenas números inteiros positivos.

### [BUG-006] Ausência de Validação de Formato de URL (CT-10 e CT-13)
* **Severidade:** Média
* **Descrição:** Os campos de "URL da Capa" e "Link de Inscrição" não validam se o conteúdo inserido é de fato um link funcional.
* **Passos para reproduzir:**
    1. No campo de URL, inserir um texto comum (ex: "meu_curso_novo").
    2. Clicar para **cadastrar o curso**.
* **Resultado Atual:** O sistema salva o texto e o dashboard apresenta imagens quebradas ou links que não levam a lugar algum.
* **Resultado Esperado:** O sistema deve validar se o texto segue o padrão de protocolo URL (http:// ou https://).

---

## 5. Uso de Inteligência Artificial

Neste desafio, utilizei a IA como uma ferramenta de **apoio consultivo**. 
* **Como utilizei:** Auxílio na estruturação da documentação e brainstorming de cenários de teste negativos.
* **Análise Crítica:** Refinei as sugestões da IA para garantir que os cenários estivessem alinhados exatamente com os campos visíveis na aplicação analisada, descartando sugestões genéricas.
