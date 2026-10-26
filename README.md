# VariSkill - Sprint 2

<br>

<p align="center">
    <a href="#objetivos"> Objetivos da Sprint </a> &nbsp;|&nbsp;&nbsp;
    <a href="#entregas"> Entregas </a> &nbsp;|&nbsp;&nbsp;
    <a href="#metricas"> Métricas do Time </a> &nbsp;|&nbsp;&nbsp;  
    <a href="#backlog"> Backlog da Sprint </a> &nbsp;|&nbsp;&nbsp;  
    <a href="#links"> Links úteis </a>
</p>

---

Na **Sprint 2** da plataforma **VariSkill**, o objetivo primordial foi consolidar a experiência pedagógica personalizada, a gamificação progressiva do estudante e a resiliência operacional da plataforma. Foram implementados o enriquecimento de perfil com interesses e dados demográficos, o sistema determinístico de níveis e faixas de XP, o mapeamento relacional de respostas com diagnóstico formativo de erros, o reconhecimento e execução de comandos locais em linguagem natural via PLN, a recomendação contextual de trilhas no fluxo conversacional, a memória contínua de sessão e estratégias de contingência e Circuit Breaker para tolerância a falhas e cotas de IA.

<span id="objetivos">

# 🎯 Objetivos da Sprint

Os requisitos funcionais atendidos nesta sprint foram:

- ✔️ **RFN01. Perfil Enriquecido do Usuário (US06):** Captura de dados demográficos (sexo, idade) e catálogo normalizado de interesses em tecnologia para direcionamento personalizado de estudos.
- ✔️ **RFN05. Recomendação Contextual de Trilhas (US07):** Sugestão interativa de trilhas no chat baseada nas preferências declaradas e histórico do estudante, com cards visuais de recomendação rápida.
- ✔️ **RFN08. Gamificação Progressiva (US08):** Evolução contínua por faixas progressivas de XP, cálculo determinístico de nível, barra de progresso visual e celebração comemorativa de level up na interface.
- ✔️ **RFN07. Mapeamento de Erros e Parecer Formativo (US09):** Registro granular das respostas por questão (`RespostaQuestao`), histórico de tentativas e motor de feedback pedagógico identificando pontos de vulnerabilidade.
- ✔️ **RFN07. Memória Pedagógica Contínua (US10):** Injeção do histórico de erros, acertos e interesses no contexto conversacional do assistente para calibrar saudações e explicações didáticas.
- ✔️ **RFN02. Comandos em Linguagem Natural via PLN Local (US11):** Despacho e atendimento instantâneo de comandos pelo chat (consulta de nível/XP e redirecionamento para próxima atividade) sem acionar LLM externa.
- ✔️ **RFN10. Resiliência e Disponibilidade da Plataforma (US12):** Circuit Breaker com controle de timeout e fallback resiliente diante de erros de rede ou esgotamento de cotas de IA (HTTP 429), garantindo que trilhas, exercícios e gamificação funcionem ininterruptamente.

<br>

---

<span id="entregas">

# 📲 Entregas

Durante a Sprint 2, a equipe refinou e entregou os épicos planejados com alinhamento contínuo às necessidades dos usuários e aos critérios de aceitação definidos com a Product Owner. A experiência de estudo foi enriquecida tanto no front-end em React 19 (com cards dinâmicos, barra de XP, modal de level up e chat resiliente) quanto no back-end em Django REST Framework (com novos models relacionais, pipeline local de PLN, cache de sessão e arquitetura com tolerância a falhas).

### RFN01: Perfil Enriquecido do Usuário
Como usuário, quero cadastrar e atualizar meus dados complementares (sexo, idade e interesses), para que minhas recomendações de trilhas e conteúdos sejam personalizadas.

### RFN05: Recomendação Contextual de Trilhas
Como usuário, quero que o assistente recomende trilhas com base no meu perfil e histórico (ou por atividade avaliativa se eu for novo), para que eu siga a jornada mais adequada ao meu nível.

### RFN08: Gamificação Progressiva de Nível e XP
Como usuário, quero evoluir de níveis de acordo com a quantidade de XP acumulada, para que eu acompanhe meu progresso visual e me sinta motivado a continuar estudando.

### RFN07: Mapeamento de Erros e Parecer Formativo
Como usuário, quero que o assistente mapeie minhas atividades e questões erradas e forneça feedback formativo, para que eu entenda minhas dificuldades e revise conteúdos pontuais.

### RFN07: Memória Pedagógica Contínua
Como estudante recorrente, quero que o assistente se lembre do meu histórico, pontos fortes e dificuldades anteriores, para que suas orientações e saudações sejam personalizadas à minha evolução.

### RFN02: Comandos em Linguagem Natural no Chat (PLN Local)
Como usuário, quero enviar comandos em linguagem natural no chat (ex: pedir próxima atividade, consultar nível e XP), para que o assistente execute a ação no sistema via PLN local sem consumir a IA externa.

### RFN10: Resiliência e Disponibilidade da Plataforma
Como usuário, quero que a plataforma permaneça rápida e disponível mesmo em momentos de instabilidade da IA, para que meus estudos e exercícios nunca sejam interrompidos.

<br>

---

<span id="metricas">

# 📈 Métricas do Time

<p>Segue abaixo o acompanhamento de execução e burndown da equipe durante a Sprint 2:</p>

<br>
    
<div align="center">
<img src="./mgt/burndown-sprint2.png" alt="Gráfico Burndown Sprint 2" />
</div>

<br>

---

<span id="backlog">

# 📃 Backlog da Sprint

| **RFN** | **Rank** | **Prioridade** | **User Story** | **Estimativa** | **Sprint** | **Critérios de Aceitação** |
| ------- | -------- | -------------- | -------------- | -------------- | ---------- | -------------------------- |
| **RFN01** | 6 | Média | Como usuário, quero cadastrar e atualizar meus dados complementares (sexo, idade e interesses), para que minhas recomendações de trilhas e conteúdos sejam personalizadas. | 3 | 2 | - Formulário de perfil com campos para sexo, idade e interesses (tags de tecnologias/áreas);<br>- Dados devidamente persistidos na entidade de usuário e tabela associativa de interesses;<br>- Endpoints da API atualizados para leitura e atualização das novas informações. |
| **RFN05** | 7 | Alta | Como usuário, quero que o assistente recomende trilhas com base no meu perfil e histórico (ou por atividade avaliativa se eu for novo), para que eu siga a jornada mais adequada ao meu nível. | 8 | 2 | - Chat analisa perfil do usuário (interesses e nível autodeclarado) e histórico de desempenho;<br>- Para novos usuários, direcionamento ou disparo de atividade avaliativa/diagnóstica;<br>- Recomendação contextual de possíveis trilhas;<br>- Visualização da jornada pedagógica com etapas e status. |
| **RFN08** | 8 | Alta | Como usuário, quero evoluir de níveis de acordo com a quantidade de XP acumulada, para que eu acompanhe meu progresso visual e me sinta motivado a continuar estudando. | 5 | 2 | - Definição de faixas de XP por nível (nível calculado deterministicamente);<br>- Barra de progresso com XP atual e XP necessário para o próximo nível;<br>- Notificação comemorativa de level up na interface. |
| **RFN07** | 9 | Média | Como usuário, quero que o assistente mapeie minhas atividades e questões erradas e forneça feedback formativo, para que eu entenda minhas dificuldades e revise conteúdos pontuais. | 5 | 2 | - Mapeamento das questões e atividades respondidas incorretamente a partir do histórico granular de respostas;<br>- Assistente contextualiza tópicos com menor taxa de acerto;<br>- Geração de parecer formativo com sugestão de revisão dos pontos fracos. |
| **RFN07** | 10 | Média | Como estudante recorrente, quero que o assistente se lembre do meu histórico, pontos fortes e dificuldades anteriores, para que suas orientações e saudações sejam personalizadas à minha evolução. | 5 | 2 | - Contexto resumido persistido na sessão mantendo histórico de erros, acertos e interesses;<br>- Assistente calibra saudações, dicas e recomendações pedagógicas utilizando essa memória. |
| **RFN02** | 11 | Alta | Como usuário, quero enviar comandos em linguagem natural no chat (ex: pedir próxima atividade, consultar nível e XP), para que o assistente execute a ação no sistema via PLN local sem consumir a IA externa. | 8 | 2 | - Pipeline de PLN local com classificação de intenções e ações sobre o corpus essencial;<br>- Execução direta de ações no banco para comandos com similaridade >= 0.70 com templates variados de resposta;<br>- Encaminhamento para a IA externa apenas de mensagens não reconhecidas localmente. |
| **RFN10** | 12 | Alta | Como usuário, quero que a plataforma permaneça rápida e disponível mesmo em momentos de instabilidade da IA, para que meus estudos e exercícios nunca sejam interrompidos. | 5 | 2 | - Payload otimizado com contexto enxuto para manter respostas ágeis;<br>- Tratamento resiliente de falhas de rede e esgotamento de cotas da API externa (HTTP 429) com mensagens amigáveis de contingência;<br>- Navegação, conteúdos, quizzes e ganho de XP 100% operacionais mesmo sem conexão com a IA. |

<br>

---

<span id="links">

# 🔗 Links úteis

- **Tags geradas em cada repositório que simbolizam o fim da 2ª sprint:** <br>
  - 🔗 [v2.0.0 BACKEND](https://github.com/SkyFlyTeam/Variskill-backend/releases/tag/v2.0.0) <br>
  - 🔗 [v2.0.0 FRONTEND](https://github.com/SkyFlyTeam/VariSkill-frontend/releases/tag/v2.0.0)
