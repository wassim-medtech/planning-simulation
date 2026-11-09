# Historique des modifications

## 2026-11-09 — Mode « Matière » et export Excel par simulation
- Nouveau mode `CAPACITE_MODE = "Matiere"` : capacité finie + disponibilité matière, mode `Plutot` forcé, toutes les vérifications actives.
  - Semi-finis fabriqués : toujours vérifiés (lots produits par les OF déjà placés) ; sinon statut `ECHOUE(matiere)`.
  - Matières achetées critiques (X3NOM `RUPTURE_0 = 1`, `TYPEARTICLE_0 = 3`) : vérifiées sur la fenêtre `[lundi de SIM_LAUNCH_DATE ; + HORIZON_MP_CRITIQUE_JOURS]` à partir du stock X3STOCK (péremption) et des réceptions X3DATERCP. Une rupture ne rejette pas l'OF : il est placé à partir de la fin de la fenêtre, sans consommer de matière.
  - Nouvelles tables lues : `X3NOM`, `X3STOCK`, `X3DATERCP`.
  - Nouvelle table écrite : `res_echecs_matiere` (OF, article critique, quantité manquante, date de disponibilité estimée).
  - Nouvelles colonnes `S_smoothing.disponibilite_matiere_ok` et `date_disponibilite_matiere` (mode Matière uniquement).
- Tous les modes :
  - `S_stock_movements` : nouvelle colonne `num_lot` ; stock cumulé arrondi à 6 décimales (plus de résidus du type -1e-10).
  - Typologie d'échec « Matière / Disponibilité matière ».
  - Diagnostic `[DIAG stock<0]` affiché quand une sortie est datée avant l'entrée du lot consommé (30 lignes max).
- Export Excel : une simulation précise (`SIM_ID_EXPORT`, `None` = la dernière), fichier `simulation_<ID_SIM>.xlsx`, onglets `S_stock_movements` et `res_echecs_matiere` ajoutés.
- Réglages du run : `Matiere`, `Plutot`, lancement et `HORIZON_DEB` au 2027-01-11, `SIM_DESC = SIM_Matiere_11_2026_FIN`.

## 2026-10-31 — Version initiale
- Mise sous contrôle de version du notebook `simulation_planning` (version utilisée pour la simulation `SIM261000018`, capacité Finie, mode Plutard, lancement 2026-10-26).
