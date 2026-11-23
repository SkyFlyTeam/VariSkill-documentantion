# VariSkill - Sprint 3

<br>

<p align="center">
    <a href="#objetivos"> Objetivos da Sprint </a> &nbsp;|&nbsp;&nbsp;
    <a href="#entregas"> Entregas </a> &nbsp;|&nbsp;&nbsp;
    <a href="#metricas"> Métricas do Time </a> &nbsp;|&nbsp;&nbsp;  
    <a href="#backlog"> Backlog da Sprint </a> &nbsp;|&nbsp;&nbsp;  
    <a href="#links"> Links úteis </a>
</p>

---

Na **Sprint 3** da plataforma **VariSkill**, o objetivo primordial foi consolidar o engajamento de longo prazo do estudante, a inteligência coletiva de resposta instantânea via busca vetorial e a evolução contínua do acompanhamento pedagógico. Foram implementados o sistema completo de ofensiva diária (*streaks*), o motor determinístico de conquistas e o inventário de cosméticos (avatares, títulos e bordas) com suporte a armazenamento em nuvem (AWS S3 e fallback local), o cache semântico de dúvidas assimiladas com `pgvector` e índice HNSW para respostas em menos de 100ms com avaliação de utilidade (👍/👎), e a síntese da memória pedagógica de longo prazo com diagnóstico visual ("Meu Raio-X de Aprendizado") e saudações dinâmicas contextualizadas do assistente Vari.

<span id="objetivos">

# 🎯 Objetivos da Sprint

Os requisitos funcionais atendidos nesta sprint foram:

- ✔️ **RFN09. Conquistas, Recompensas e Streak Diário (US11):** Registro diário de estudos com controle determinístico de streaks, catálogo e motor de concessão de conquistas e itens cosméticos (avatares, títulos e bordas), armazenamento de assets integrado à AWS S3 com fallback local, modal comemorativo de desbloqueio e gestão de inventário no perfil.
- ✔️ **RFN06. Dúvidas Assimiladas e Cache Semântico com pgvector (US12):** Ingestão assíncrona com proteção anti-duplicação do par pergunta do aluno + resposta didática da IA no banco vetorial (`pgvector`), priorizando a busca por similaridade local (< 100ms) com indicador visual de resposta instantânea no chat e coleta de feedback de utilidade (👍/👎).
- ✔️ **RFN07. Memória Pedagógica Contínua de Longo Prazo (US13):** Consolidação automática dos pontos fortes e tópicos de dificuldade do estudante a partir do histórico de submissões (`RespostaQuestao`) ao concluir módulos, exposição via endpoint de diagnóstico pedagógico, exibição do card "Meu Raio-X de Aprendizado" no perfil e calibração de saudações, dicas e contexto conversacional do assistente Vari.

<br>

---

<span id="entregas">

# 📲 Entregas

Durante a Sprint 3, a equipe concluiu e validou todos os épicos finais do produto em alinhamento com o Product Owner e os critérios de definição de pronto (DoD). A solução foi aprimorada no front-end em React 19 e TypeScript (com o badge interativo de streak no header, abas de conquistas e inventário de cosméticos, modal comemorativo de conquista desbloqueada, badge de resposta instantânea da base de conhecimento com feedback de utilidade e o card "Meu Raio-X de Aprendizado") e no back-end em Django REST Framework (com o `StreakService`, `GamificationEngine`, integração `S3StorageService`, entidade vetorial `DuvidaAssimilada` com índice HNSW, `SemanticCacheService` e `PedagogicalMemoryService`).

### RFN09: Conquistas, Inventário de Cosméticos e Streak Diário
Como usuário, quero desbloquear conquistas, acumular recompensas no meu inventário e manter um streak diário, para que meu engajamento seja reconhecido e exibido no perfil.

### RFN06: Dúvidas Assimiladas e Cache Semântico (pgvector)
Como estudante, quero que as dúvidas explicadas pelo assistente fiquem salvas na base de conhecimento, para que perguntas semelhantes sejam respondidas instantaneamente sem lentidão de rede.

### RFN07: Memória Pedagógica Contínua e Diagnóstico de Longo Prazo
Como estudante recorrente, quero que o assistente se lembre do meu histórico, pontos fortes e dificuldades anteriores, para que suas orientações e saudações sejam personalizadas à minha evolução.

<br>

---

<span id="metricas">

# 📈 Métricas do Time

<p>Segue abaixo o acompanhamento de execução e burndown da equipe durante a Sprint 3:</p>

<br>
    
<div align="center">
<img src="./mgt/burndown-sprint3.png" alt="Gráfico Burndown Sprint 3" />
</div>

<br>

---

<span id="backlog">

# 📃 Backlog da Sprint

| **RFN** | **Rank** | **Prioridade** | **User Story** | **Estimativa** | **Sprint** | **Critérios de Aceitação** |
| ------- | -------- | -------------- | -------------- | -------------- | ---------- | -------------------------- |
| **RFN09** | 11 | Média | Como usuário, quero desbloquear conquistas, acumular recompensas no meu inventário e manter um streak diário, para que meu engajamento seja reconhecido e exibido no perfil. | 8 | 3 | - Registro diário de acesso/atividades com contador de streak no dashboard;<br>- Regras determinísticas para desbloqueio de cosméticos (avatares, medalhas e títulos) do catálogo de recompensas;<br>- Inventário do aluno registrando as conquistas e itens desbloqueados com opção de equipar no perfil. |
| **RFN06** | 12 | Média | Como estudante, quero que as dúvidas explicadas pelo assistente fiquem salvas na base de conhecimento, para que perguntas semelhantes sejam respondidas instantaneamente sem lentidão de rede. | 8 | 3 | - Ingestão assíncrona no banco de dados do par pergunta do aluno + resposta didática gerada pela IA vinculada ao módulo/atividade;<br>- Busca por similaridade local com índice HNSW no `pgvector` priorizando as dúvidas já assimiladas pelo sistema;<br>- Redução drástica de chamadas à IA externa, resposta imediata (< 100ms) para dúvidas recorrentes e avaliação de utilidade no chat. |
| **RFN07** | 13 | Baixa | Como estudante recorrente, quero que o assistente se lembre do meu histórico, pontos fortes e dificuldades anteriores, para que suas orientações e saudações sejam personalizadas à minha evolução. | 5 | 3 | - Consolidação da síntese pedagógica após fechamento de cada módulo com histórico de dificuldades e pontos fortes;<br>- Exibição do diagnóstico no card "Meu Raio-X de Aprendizado" na tela de perfil;<br>- Assistente utiliza a memória pedagógica para calibrar saudações dinâmicas, recomendações e novos feedbacks ao longo do tempo. |

<br>

---

<span id="links">

# 🔗 Links úteis

- **Tags geradas em cada repositório que simbolizam o fim da 3ª sprint:** <br>
  - 🔗 [v3.0.0 BACKEND](https://github.com/SkyFlyTeam/Variskill-backend/releases/tag/v3.0.0) <br>
  - 🔗 [v3.0.0 FRONTEND](https://github.com/SkyFlyTeam/VariSkill-frontend/releases/tag/v3.0.0)
