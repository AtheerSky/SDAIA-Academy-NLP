# Bayan synthetic datasets (v2 — harder)

All data is synthetic teaching data; no real citizen records are used. File names and columns are identical to v1.

What changed vs v1 (v1 had \~71 repeated templates, so TF-IDF scored 1.000):

- bayan\_feedback.csv (12,000 rows; 6,000 ar / 6,000 en; 3,200 citizens): \~98% unique texts. Messages are built from direct complaints, indirect/scenario complaints, vague complaints (≈16%, often with no topic word) and compound messages mentioning two topics (label \= the first/primary one). Topics share vocabulary (e.g. "portal" appears in billing, digital\_services, permits…). \~3% of `topic` labels are noisy (a confusable topic), \~8% of `sentiment` labels are noisy, and `service_entity` equals `topic` only \~86% of the time (routing entity — do NOT use it as a feature). Citizens send repeated/follow-up messages (≈35% near-duplicates of their previous message) → group the split by `citizen_id`. Rare synonyms, typos, tatweel, elongation, diacritics, Arabic-Indic digits, emoji, links, phone/ID/e-mail PII are injected. Arabic dialects (Gulf/MSA/Levantine/Egyptian) are produced by phrase mapping from MSA — have a native speaker review them. Expected (measured): TF-IDF+LinearSVC macro-F1 ≈ 0.80–0.82 on the citizen-grouped split (Lab 3a seeds).  
- bayan\_raw\_sample.csv: 200 random rows of the feedback file (same columns).  
- pii\_test\_set.csv: 60 cases (20 PHONE, 20 NATIONAL\_ID, 20 EMAIL) in several formats (plain, spaced, dashed, inside sentences).  
- bayan\_ner\_4000.csv: 4,000 sentences; BIO tags PERSON / LOCATION / SERVICE with multi-token entities (B-/I-), districts, Arabic clitic locations (e.g. "بجدة"), ambiguous names (Noor, Rose, نور, ورد) and \~8% sentences with no entity.  
- bayan\_service\_docs.csv: 8 documents, 6 facts each.  
- bayan\_qa\_600.jsonl / qa\_smoke\_set.json: SQuAD-2-style; 510 answerable (exact character spans verified) \+ 90 unanswerable (related questions the document does not answer, or a question about another document). Contexts are random 3–6 fact subsets, sometimes with a distracting sentence from another document.  
- bayan\_cases.csv: 20,000 cases (2,500 per topic, 10,000 ar / 10,000 en). Each description ends with district \+ date, so many cases share the same problem but differ in place/date (hard negatives). \~8% are unresolved (`resolved=False`).  
- bayan\_queries.jsonl: 150 judged queries: 130 answerable (≈37% cross-language: query language ≠ case language) and 20 no-answer (10 out-of-domain, 10 in-domain wording about a city absent from the case base); no-answer rows have relevant\_case\_id \= null.  
- bench\_mix.npy: 2,000 texts for latency benchmarking (short, medium and long concatenations).

Fidelity note: NER uses only PERSON, LOCATION, SERVICE. Retrieval/QA/Transformer gains are not guaranteed: students must measure and report their own results.