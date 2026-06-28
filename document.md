# English for Success — Plano de Construção do App (Bíblia do Projeto)

> **Documento-mestre da construção do app. Salve este arquivo.**
> Sempre que você abrir um chat novo com o Claude pra continuar, **cole este documento inteiro** (ou pelo menos a **Seção 1**) como primeira mensagem. Assim o novo Claude entende o projeto na hora e o fluxo de produção não se perde.

---

## 1. Snapshot (cole isto num chat novo)

**Produto:** English for Success — app de inglês com IA para brasileiros que querem crescer na carreira, nos negócios e morar fora. Foco em **Business English** e preparação para o **IELTS**.

**Mentor de IA:** **"Delagassa Mentor"** — personagem com voz **motivadora**, fala em português e inglês, disponível 24h. Conversa, corrige na hora e comemora cada evolução.

**Fundador:** Jean (sobrenome **Delagassa**). Trabalha 100% pelo **iPhone**. Fluxo: edita no GitHub → Vercel publica sozinho. Prefere poucos arquivos e simplicidade. Valoriza **honestidade com o cliente** acima de tudo.

**Preços:** Grátis (com anúncios, limite diário) · **Pro R$49,90/mês** (sem anúncios, ilimitado). Cancela quando quiser. Pagamento via **Stripe**, cartão de crédito; conversão de moeda automática pra quem está fora do Brasil.

**Identidade visual (o app TEM que combinar com a landing):**
- Estilo: minimalista premium (Apple/Linear), **fundo claro**, muito espaço em branco.
- Fonte: **Inter** (títulos em bold, tracking apertado; palavra de destaque em navy/azul).
- Cores: `--ink #0B0E14` · `--navy #13213F` · `--blue #2E54E8` · `--blue-bright #5B82FF` · `--slate #5A6577` · `--mist #F6F8FB` · `--paper #FFFFFF`.
- Logo: retrato ilustrado do Jean (círculo com anel dourado) — usado **também como avatar do Delagassa**.

**Voz do Delagassa (referência — manter no prompt de sistema da IA):** motivador; corrige sem desmotivar; transforma erro em "próximo passo"; empurra pra frente ("bora", "vamos", "confia"); explica em português; mistura PT/EN; sempre preciso na correção. Exemplos:
- "Tá quase lá! 🙌 É *I agree* (não *I'm agree*) — 'agree' já é o verbo. Você já monta frase de reunião sozinho. Bora pra próxima!"
- "É assim que se evolui! 🔥 Vou puxar vocabulário de negotiation no seu nível e corrigir cada detalhe. Confia: logo isso vira automático. Vamos!"

**Trilhas de aprendizado:** Foundation · Everyday English · UK Life English · Career English · Business English · Entrepreneur English · + preparação IELTS.

**Landing page:** no ar. Arquivo único `index.html`, projeto Vercel **`english-for-success-2`** (separado do app). É a referência visual do app.

**Status atual:** Planejamento concluído. **Próximo: Fase 0.**

---

## 2. O que o app precisa entregar

**Núcleo (MVP — o coração que faz jus à landing):**
- Cadastro/login e perfil do aluno (nome, objetivo, nível).
- **Chat com o Delagassa** (IA motivadora, correção, PT/EN, com memória) — o coração.
- Estrutura básica de trilhas/aulas + acompanhamento de progresso.
- Gate: Grátis (limite + anúncio) vs Pro (pago, ilimitado, sem anúncio).

**Depois (diferenciais da landing):**
- Voz e pronúncia (falar e receber feedback).
- Simulador de IELTS (band estimada).
- Vocabulário (flashcards, repetição espaçada).
- Gamificação (XP, sequência, níveis).
- Certificado de conclusão (PDF + QR Code).

---

## 3. Arquitetura recomendada

Princípio: **simples de editar pelo iPhone, segura e profissional.**

- **Frente (o que o aluno vê):** HTML/CSS/JS, no mesmo espírito da landing (poucos arquivos, fácil de colar no GitHub). Reaproveita cores e fonte da landing.
- **Login + banco de dados:** **Supabase** (conta grátis). Cuida de cadastro, login e de guardar os dados do aluno (perfil, progresso, histórico de conversa) com segurança.
- **Cérebro de IA + pagamento:** **Funções serverless no Vercel** (pasta `/api`). Arquivos pequenos que falam com a OpenAI (IA do Delagassa) e com o Stripe **sem expor as chaves secretas**.
  - ⚠️ **Regra de ouro:** chave de API NUNCA no código da frente. Sempre nas **variáveis de ambiente do Vercel**.

**Por que assim:** é o caminho mais próximo do que você já fez na landing, com o mínimo de arquivos, mas seguro e escalável o suficiente pra validar e lançar. Se o app crescer muito, dá pra migrar pra Next.js depois.

*(Alternativa robusta pro futuro: Next.js — mais profissional, porém mais arquivos; só recomendo com o GitHub Codespaces aberto.)*

---

## 4. As Etapas (uma de cada vez)

**Fase 0 — Fundação**
- Objetivo: pipeline funcionando + casca do app com a cara da landing.
- Entregável: app vazio, porém estilizado e publicado (repo + Vercel + Supabase criados).
- Pronto quando: você acessa a URL e vê a casca do app no ar.

**Fase 1 — Cadastro e Login**
- Objetivo: aluno cria conta, faz login, responde o onboarding (objetivo, nível).
- Entregável: autenticação funcionando, perfil salvo no Supabase.
- Pronto quando: você cria uma conta de teste e ela aparece no Supabase.

**Fase 2 — Delagassa Mentor (o coração)**
- Objetivo: chat com a IA — voz motivadora, correção, PT/EN, com memória.
- Entregável: função `/api` falando com a OpenAI + tela de chat; histórico salvo.
- Pronto quando: você conversa com o Delagassa e ele corrige e motiva de verdade.

**Fase 3 — Trilhas e Aulas**
- Objetivo: conteúdo estruturado (Foundation, Business, IELTS...) + progresso.
- Entregável: telas de trilha/aula + acompanhamento.
- Pronto quando: dá pra concluir uma aula e o progresso fica salvo.

**Fase 4 — Monetização**
- Objetivo: ligar o caixa.
- Entregável: Stripe (Pro R$49,90) + webhook + gate Grátis/anúncio vs Pro.
- Pronto quando: uma assinatura de teste libera o Pro e tira os anúncios.

**Fase 5 — Diferenciais** *(cada item é uma sub-etapa própria)*
- Voz/pronúncia · Simulador IELTS · Vocabulário/flashcards · Gamificação · Certificado.

**Fase 6 — Polimento e Lançamento**
- Testes no celular · performance · LGPD/privacidade · tratamento de erros · conectar app ↔ landing (ex.: `app.seudominio`) · lançamento.

---

## 5. Regras da Construção (pra nada travar o fluxo)

1. **Uma fase por vez.** Só começa a próxima quando a atual estiver publicada e testada.
2. **Cada fase entrega algo que funciona e está no ar.** Nada de "metade pronto".
3. **Chaves secretas só nas variáveis de ambiente do Vercel.** Nunca no código da frente.
4. **Não mexer na landing.** Ela é projeto separado e já está no ar vendendo.
5. **Mobile-first e fiel à identidade** (cores, fonte, voz motivadora do Delagassa).
6. **Se travar, simplifica.** Melhor uma versão menor no ar do que uma grande quebrada.
7. **Atualize o Progresso (Seção 8)** ao fim de cada fase, anotando a URL e observações.

---

## 6. Decisões já tomadas
- Marca: **English for Success** · Mentor: **Delagassa** (voz motivadora).
- Preço: **Grátis com anúncio / Pro R$49,90/mês**, cartão, cancela quando quiser.
- **Sem depoimento falso**; certificado é **de conclusão** (não IELTS oficial).
- Landing pronta e no ar (projeto separado `english-for-success-2`).

---

## 7. O que falta decidir / preparar
- **Como editar o app:** Codespaces (editor completo no navegador) ou copy-paste como na landing.
- Criar conta no **Supabase** (grátis) — login + banco de dados.
- Criar conta na **OpenAI** com billing (a IA é paga por uso) — é o **custo principal** do app.
- *(Depois)* Conta **Stripe** para receber pagamentos · domínio próprio.

---

## 8. Progresso
- [ ] **Fase 0** — Fundação
- [ ] **Fase 1** — Cadastro e Login
- [ ] **Fase 2** — Delagassa Mentor
- [ ] **Fase 3** — Trilhas e Aulas
- [ ] **Fase 4** — Monetização
- [ ] **Fase 5** — Diferenciais
- [ ] **Fase 6** — Polimento e Lançamento

*(Marque o que terminar e anote a URL/observações de cada fase.)*
