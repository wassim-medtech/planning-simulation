# Simulation de planification S&OP

Notebook Microsoft Fabric (PySpark) qui simule la planification des OF à partir du lakehouse `Planning_Lakehouse`.

## Contenu

| Fichier | Rôle |
|---|---|
| `simulation_planning.ipynb` | Groupage des OF, lissage et planification (capacité finie / infinie), écriture des tables `S_*`, export Excel |

## Tables lues (lecture seule)
`sim_of_work`, `sim_nom_child`, `SIM_POSTE_CAPA`, `X3OF`, `X3ITM`

## Tables écrites (append, une ligne par `ID_SIM`)
`Simulation`, `S_grouped_needs`, `S_smoothing`, `S_smoothing_operations`, `S_weekly_capacity`,
`S_groups_anchors`, `S_produced_quantities`, `S_stock_movements`, `S_summary_division_status`,
`S_failure_details`, `S_failure_summary_typologie`, `S_failure_summary_top`

## Paramètres principaux (bloc en tête du notebook)
- `CAPACITE_MODE` : `Finie` / `Infinie`
- `MODE_PLANIF` : `Plutot` / `Plutard`
- `SIM_LAUNCH_DATE` : aucun OF planifié avant le lundi de cette semaine
- `SIM_ARRETS` : périodes d'arrêt (tous postes)
- `VERIF_STOCK`, `VERIF_ECART_OPS`, `VERIF_FENETRE` : vérifications activables
- `HORIZON_DEB` / `HORIZON_FIN` : filtre sur les dates de besoin

## Méthode de travail
1. Chaque modification fait l'objet d'un commit avec un message clair (quoi + pourquoi).
2. Les sorties d'exécution ne sont pas versionnées (seul le code compte).
3. Les grosses évolutions passent par une branche, puis une Pull Request vers `main`.
4. Le fichier `CHANGELOG.md` résume les changements fonctionnels.
