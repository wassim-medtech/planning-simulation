# Historique des modifications

## 2026-10-31 — Évolution de la quantité à fabriquer par article
- Nouveaux paramètres : `EVOL_QTE_PAR_ARTICLE` (ex. `{"PF001234": 10}` = +10 %), `EVOL_QTE_TABLE` (table optionnelle `Article`, `Pct`), `EVOL_QTE_PROPAGER_SF`, `EVOL_QTE_ARRONDI`.
- La quantité de tous les OF de l'article est multipliée par (1 + %), et les heures de leurs opérations (`ChargeCalculee`) suivent dans la même proportion.
- Propagation aux composants (SF) via la nomenclature : chaque SF reçoit le surplus réellement consommé par ses parents, réparti au prorata sur ses OF de l'horizon (ex. surplus 60 pour 1 000 → +6 %), sur tous les niveaux. Un article listé explicitement garde son propre %.
- Nouvelles colonnes de trace : `Simulation.EVOL_QTE`, `S_grouped_needs.Qty_Origine` / `Coef_Evol`, `S_smoothing.qty_origine` / `coef_evol`, `S_smoothing_operations.Charge_Origine`, `S_produced_quantities.QuantityDemandee_Origine`.
- Sans article renseigné (dictionnaire vide), les résultats sont identiques à la version précédente.

## 2026-10-31 — Version initiale
- Mise sous contrôle de version du notebook `simulation_planning` (version utilisée pour la simulation `SIM261000018`, capacité Finie, mode Plutard, lancement 2026-10-26).
