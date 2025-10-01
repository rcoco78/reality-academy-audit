## Audit Marketing & Growth 360 — Reality Academy

### Sommaire
- [Contexte et objectifs](#contexte-et-objectifs)
- [Diagnostic synthétique](#diagnostic-synthétique)
- [Analyse détaillée par levier](#analyse-détaillée-par-levier)
- [Plan d’exécution priorisé (4–6 semaines)](#plan-dexécution-priorisé-4–6-semaines)
- [KPI à suivre (hebdo)](#kpi-à-suivre-hebdo)
- [Risques & mitigations](#risques--mitigations)
- [Ce que je prends en charge (expertise)](#ce-que-je-prends-en-charge-expertise)
- [Ce que vous pouvez déléguer](#ce-que-vous-pouvez-déléguer)
- [Annexe — Faits marquants](#annexe--faits-marquants)
- [Annexes détaillées](#annexes-détaillées)
- [Questions ciblées (à valider)](#questions-ciblées-à-valider)

### Prochaines étapes (executive summary)
- Valider cette semaine: schéma d’états `Sellsy`, règles stop‑nurturing Make, création domaine secondaire outbound.
- Lancer sous 14 jours: AB tests LinkedIn « Calendrier RH » et séquences outbound v1 (2 personas).
- Mettre en place: formulaires durcis (email pro, phone regex, reCAPTCHA, double opt‑in) et dashboard funnel.

### Contexte et objectifs
- **Périmètre**: inbound (site, SEO, ressources), outbound (emailing Lemlist), cold calling (SDR), salons (Préventica), ads (LinkedIn/Meta), automatisations (Make ↔ Sellsy/Notion/Aircall/Calendly).
- **Objectif**: fournir un diagnostic actionnable qui aligne marketing et sales, fiabilise la donnée et priorise les leviers ROI court terme.

### Diagnostic synthétique
- **Gouvernance & data**: outils fragmentés (Sellsy, Notion, Lemlist, Mailjet, Make), peu de journalisation centralisée dans `Sellsy`; pas de vue de funnel bout‑à‑bout (source ➔ opp ➔ revenu).
- **Site & conversion**: CTA RDV sous‑exploité; formulaires sans garde‑fous (email pro, regex phone, double opt‑in); friction dans l’attribution et le stop des campagnes.
- **SEO**: blog non indexé correctement; canoniques/redirections incohérentes; courbe SEO non linéaire; backlog d’articles non publiés.
- **Automatisations (Make)**: migration incomplète, scénarios instables/désactivés; absence de "stop nurturing" quand un lead passe SQL/Meeting.
- **Outbound**: campagnes éclatées par commerciaux; manque de normalisation (déduplication CRM, exclusions clients, cadences, CTA); risque délivrabilité (domaine principal).
- **Cold calling**: meilleur canal actuel (10–15 RDV/sem) mais peu de feedback loop structuré vers marketing.
- **Ads**: LinkedIn « Calendrier RH » performant (CPL ~16,29 €; créas fond blanc <10 €). Campagnes « Catalogue » non performantes (offre trop générique, ciblage dispersé, budgets sous‑critiques).

### Analyse détaillée par levier

#### 1) Gouvernance, données et pilotage
- Problème: absence de standard d’états et d’événements; reporting éclaté; décisions lentes.
- Recommandations:
  - Schéma d’états commun `New → MQL → SQL → Meeting → Proposal → Won/Lost` (horodaté).
  - Journalisation unifiée dans `Sellsy`: source, campagne, UTM, score, dernière action, owner.
  - Tableau de bord hebdo: visites, leads par source, MQL, SQL, meetings, win rate, CAC/ canal.

#### 2) Site, formulaires et conversion
- Constat: RDV Calendly pas assez visible; validation faible (emails free, numéros fantaisistes); absence de double opt‑in.
- Recos concrètes:
  - Mettre un **CTA sticky "Prendre RDV"** (Calendly) sur tout le site; A/B test contact vs RDV direct.
  - Durcir formulaires: denylist emails free, regex téléphone FR/INT, reCAPTCHA, double opt‑in Mailjet.
  - Copy orientée bénéfices + social proof; progressive profiling (réduire la friction initiale).

#### 3) SEO et contenu
- Constat: canoniques/redirections incohérentes; blog non indexé; création de pages irrégulière.
- Recos:
  - Correctifs techniques: canoniques, 301, sitemap, Core Web Vitals, indexation blog.
  - Calendrier éditorial par thématique (10 piliers); maillage interne vers pages offres/ressources.
  - Production assistée (IA outillée) sous contrôle éditorial: structure, maillage, CTA, preuves.

#### 4) Automatisations (Make)
- Constat: scénarios clés (ressources, scoring, calendly, aircall) sans stop‑rules; fiabilité perfectible.
- Recos:
  - Rules cross‑outils: si `Sellsy.stage ≥ SQL`, alors stop nurturing Mailjet/Lemlist; si rendez‑vous annulé, décrément score; si no‑show, relance dédiée.
  - Healthcheck: monitoring scénarios, alerting Slack, retry/backoff, logs et QA.

#### 5) Outbound (Lemlist)
- Constat: campagnes hétérogènes, gouvernance floue, risque délivrabilité.
- Recos:
  - **Domaine secondaire** (SPF/DKIM/DMARC/BIMI), warm‑up, 2–4 inbox dédiées/persona; montée en charge progressive.
  - Séquences standardisées par persona (RH, HSE/QSE, Handicap, Cyber), cadence et CTA unique (demo 20 min).
  - Pipeline data: déduplication vs `Sellsy` (clients/opp ouvertes), enrichissement (titre, seniorité, téléphone), règles d’exclusion.
  - Routage des réponses vers commerciaux; tagging auto dans `Sellsy`.

#### 6) Ads (LinkedIn/Meta)
- Constat: « Calendrier RH » fonctionne (fond blanc top CPL); « Catalogue » ne convertit pas.
- Recos:
  - Capitaliser « Calendrier RH »: AB tests 14 jours (créa fond blanc vs variantes; audience RH FR/EN vs pôles; lead gen natif vs LP), budget suffisant/variante.
  - Repackager « Catalogue » en **offre utile** (kit RH + replay webinar + template); ciblage par fonction plutôt que titres trop pointus.

#### 7) Salons (Préventica & co.)
- Constat: collecte par scan efficace; manque de playbook pré/post; mesure partielle.
- Recos:
  - Pré‑salon: listes qualifiées, warm‑up (invitation démo/stand), retargeting.
  - Post‑salon: import + tagging source; séquence J+1 / J+7 / J+21; intégration `Sellsy` et stop‑rules Make.

### Plan d’exécution priorisé (4–6 semaines)

- Semaine 1
  - Valider schéma d’états & événements `Sellsy`.
  - Implémenter stop‑rules Make + healthcheck & alerting.
  - Durcir formulaires (email pro, phone regex, reCAPTCHA, double opt‑in).

- Semaine 2
  - Créer domaine secondaire + boîtes dédiées + warm‑up.
  - Déployer séquences outbound v1 (2 personas) + pipeline déduplication vs `Sellsy`.
  - Lancer AB test « Calendrier RH » (créa, audience, form natif vs LP) avec budget par variante.

- Semaine 3
  - Dashboard hebdo funnel complet (marketing → sales → revenu).
  - Correctifs SEO techniques (canoniques/redirs/sitemap); publier 2–3 articles ciblés.

- Semaines 4–6
  - Étendre outbound (2 personas de plus) et ajuster volumétrie.
  - Itérer ads (optimiser CPL et qualité); standardiser créas gagnantes.
  - Playbook salons: pré/post + mesure; capitaliser sur retargeting.

### KPI à suivre (hebdo)
- **Acquisition**: sessions, sources, CTR ads, CPL (par canal/offre), coût par meeting.
- **Funnel**: Leads, MQL, SQL, Meetings, Proposal, Won; taux de conv. inter‑étapes.
- **Emailing**: délivrabilité (open rate by provider), reply rate, bounce, spam rate.
- **Sales**: win rate, cycle, ARR par source/campagne.

### Risques & mitigations
- **Délivrabilité**: montée de volume ➔ warm‑up, domaine secondaire, limites quotidiennes.
- **Qualité de data**: déduplication stricte + exclusions CRM à l’import; QA hebdo.
- **Fiabilité Make**: monitoring + alerting + runbooks; versionner scénarios critiques.

### Ce que je prends en charge (expertise)
- Orchestration RevOps: états, événements, routage stop‑rules, QA des scénarios Make.
- Outbound à l’échelle: domaine secondaire, séquences persona‑driven, pipeline data, reporting unifié.
- Optimisation conversion: formulaires robustes, UX RDV, copies/CTA testés vite, landing rapides.
- Méthode d’expérimentation: sprints AB (ads, emails, pages), seuils stat, décisions go/no‑go.

### Ce que vous pouvez déléguer
- Technique SEO/Indexation (canoniques, redirections, performances, indexation blog).
- Production créative Ads (déclinaisons multi‑formats & itérations rapides).
- Data ops prospection (scraping salons/listes, enrichissement, normalisation & QA).
- Mise en place initiale Make (scénarios complexes) avec handover documenté.

### Annexe — Faits marquants
- LinkedIn « Calendrier RH »: 664 conv., CPL moyen 16,29 €; créas fond blanc top performer (<10 € CPL).
- « Catalogue »: CTR faible, 0 lead; offre perçue faible/utilité insuffisante; budgets trop dispersés.
- CSV QVCT: statuts variés (opens/clicks/replies/unsub); nombreuses grandes comptes; nécessité de déduplication et d’exclusions.
- Entretiens: cold call = canal fort; data silotée; manque de stop‑rules; blog non indexé + problèmes canoniques.

### Annexes détaillées
- **Scénario Make — Calendly Esteban**
  - Déclencheur: `calendly:watchInvitees`; extraction des champs (prenom, nom, email, note, date_rdv, statut, société, annulation).
  - Logique: recherche `Sellsy` par email ➔ création/mise à jour contact + opportunité, scoring, gestion annulation (à compléter pour no‑show).
  - Reco: ajouter stop‑rule (stage ≥ SQL) et décrément score sur annulation; log d’audit + Slack alert.
- **Scénario Make — Appel tagé (Aircall → Sellsy)**
  - Déclencheur: `aircall:watchCalls`; parsing numéro; mise à jour tag + score selon tag.
  - Reco: normaliser référentiel de tags; empêcher écrasement des tags précédents; mapper tags→actions (stop/continue campagne) dans `Sellsy`.
- **Scénario Make — Appel commenté (notes)**
  - Agrégation commentaires datés; enrichissement contact/opportunité dans `Sellsy`.
  - Reco: limiter taille/commentaires; créer champ « Dernière note SDR » et historique propre; déclencher tâches follow‑up.
- **Scénario Make — Webflow formulaires (Ressources/Newsletter)**
  - Déclencheur Webflow; mapping robuste des champs (nom, prénom, email, téléphone, entreprise, consentement NL…)
  - Reco: valider email pro, regex téléphone, double opt‑in; mise à jour `Sellsy` + Notion (temp) et scoring cohérent par ressource.
- **Outbound — Lemlist (campagnes 3 & 4 + CSV QVCT)**
  - Observations: messages thématiques (sécurité routière; preuve sociale grands groupes; proposition démo avec créneaux précis).
  - Reco: séquences par persona (RH vs HSE/QSE), CTA unique, renforcer personnalisation (icebreaker société), exclure clients/opp ouvertes, cadencer 5–7 touches, routage réponses vers AE.

### Questions ciblées (à valider)
- Ads: focus Q4 sur volume leads « Calendrier RH » ou RDV direct ? Budget test/variante/sem ?
- Automatisations: liste d’événements `Sellsy` disponibles; mainteneur Make et fenêtre de corrections.
- Copywriting: angles/preuves validés par persona; logos/cas disponibles.
- Outbound: go domaine secondaire; nombre d’inbox; volumétrie cible S2–S3.
- Base de données: export clients actuel pour exclusions; statut de la base HSE/QSE 9k (fraîcheur/consentements).

---


