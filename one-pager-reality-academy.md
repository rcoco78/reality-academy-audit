## Reality Academy — One‑Pager Audit 360 (Synthèse exécutive)

### Enjeux clés
- Écosystème éclaté: `Sellsy`, `Make`, `Notion`, `Lemlist`, `Mailjet` sans journalisation unifiée.
- Conversion inbound perfectible: formulaires peu filtrants, CTA RDV sous‑exploité, stop‑rules absentes.
- Outbound à structurer: délivrabilité (domaine principal), séquences hétérogènes, déduplication CRM.
- Base de données inexistante/non entretenue: faible volumétrie exploitable, champs non normalisés, personnalisation quasi nulle.

### 3 priorités (30 jours)
1) Data & Orchestration
- Schéma d’états unifié: `New → MQL → SQL → Meeting → Proposal → Won/Lost`.
- Journalisation marketing → `Sellsy` (source, UTM, score, dernière action).
- Stop‑rules Make: stage ≥ SQL → stop nurturing; annulé → décrément score; no‑show → relance dédiée.

2) Conversion & Formulaires
- CTA sticky « Prendre RDV » (Calendly) sur tout le site; test contact vs RDV direct.
- Durcir formulaires: denylist emails free, regex téléphone, reCAPTCHA, double opt‑in Mailjet.

3) Outbound industrialisé
- Domaine secondaire + warm‑up; 2–4 inbox dédiées par persona.
- Séquences normalisées (RH, HSE/QSE, Handicap, Cyber), 5–7 touches, CTA unique « démo 20 min ».
- Déduplication vs `Sellsy` (clients/opp), enrichissement.
 - Base maîtresse unique: schéma contacts/entreprises, champs normalisés; collecte continue + QA hebdo.

### Quick wins Ads (14 jours)
- Capitaliser « Calendrier RH »: AB tests (fond blanc vs variantes, RH vs pôles, lead gen natif vs LP), budget suffisant/variante.
- Repack « Catalogue » en offre utile (kit + replay + template) et ciblage par fonction.

### Plan d’exécution (S1→S4)
- S1: états `Sellsy`, stop‑rules Make, formulaires durcis, schéma base maîtresse + règles de dédup.
- S2: domaine secondaire + inbox, séquences v1 (2 personas), AB test « Calendrier RH ».
- S3: dashboard funnel hebdo, correctifs SEO, 2–3 articles ciblés, collecte continue + enrichissement.
- S4–S6: scale outbound (personas), itérations ads, playbook salons.

### KPI hebdo
- Acquisition: sessions, sources, CTR, CPL, coût/meeting.
- Funnel: Leads, MQL, SQL, Meetings, Proposal, Won.
- Emailing: open/reply/bounce/spam; délivrabilité.
- Sales: win rate, cycle, ARR par source.
 - Data health: % emails pro, bounce hard, % contacts enrichis, doublons évités.

### Risques & parades
- Délivrabilité: warm‑up + domaine secondaire + limites quotidiennes.
- Qualité data: déduplication stricte + exclusions + QA hebdo.
- Fiabilité Make: monitoring + alerting + runbooks.
