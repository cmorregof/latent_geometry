# Full-data latent geometry summary

This report audits the geometry of local AntigenLM embeddings. It does not generate sequences, optimize mutations, or reproduce AntigenLM forecasting figures.

## Cache and data

- cache: `results/embeddings_cache_full_all_available.pkl`
- embeddings: `(111756, 384)`
- deduplicated HA+NA points for TwoNN/temporal locality: `82,306`

## Spearman correlations

Pairwise correlations are estimated by random pair sampling within subtype, not by the full quadratic set of all pairs.

| metric | subtype | rho mean | rho sd | valid pairs mean | omitted pairs mean |
|---|---|---:|---:|---:|---:|
| Temporal | H1N1 | 0.0612 | 0.0009 | 200000 | 0 |
| Temporal | H3N2 | 0.1540 | 0.0008 | 200000 | 0 |
| Hamming HA | H1N1 | 0.8280 | 0.0009 | 199914 | 86 |
| Hamming HA | H3N2 | 0.6082 | 0.0005 | 199989 | 11 |
| Hamming HA+NA | H1N1 | 0.8538 | 0.0006 | 199903 | 97 |
| Hamming HA+NA | H3N2 | 0.6678 | 0.0014 | 199538 | 462 |

## PCA effective dimension

| group | n | n80 | n90 | n95 | n99 | participation ratio | top10 EVR |
|---|---:|---:|---:|---:|---:|---:|---|
| global | 111,756 | 2 | 2 | 3 | 10 | 1.91 | 0.6893, 0.2128, 0.0517, 0.0135, 0.0081, 0.0058, 0.0028, 0.0027, 0.0021, 0.0016 |
| H1N1 | 46,125 | 1 | 2 | 3 | 11 | 1.43 | 0.8285, 0.1097, 0.0225, 0.0080, 0.0076, 0.0043, 0.0035, 0.0019, 0.0017, 0.0014 |
| H3N2 | 65,631 | 1 | 3 | 5 | 16 | 1.53 | 0.8037, 0.0679, 0.0482, 0.0232, 0.0123, 0.0105, 0.0055, 0.0047, 0.0030, 0.0027 |

## TwoNN sensitivity

| sample size | trim | dimension mean | dimension sd | R2 mean |
|---:|---:|---:|---:|---:|
| 5,000 | 0.01 | 3.893 | 0.076 | 0.9809 |
| 5,000 | 0.05 | 5.497 | 0.130 | 0.9717 |
| 10,000 | 0.01 | 3.880 | 0.041 | 0.9785 |
| 10,000 | 0.05 | 5.494 | 0.095 | 0.9723 |
| 20,000 | 0.01 | 3.854 | 0.042 | 0.9777 |
| 20,000 | 0.05 | 5.449 | 0.040 | 0.9711 |
| 50,000 | 0.01 | 3.904 | 0.075 | 0.9799 |
| 50,000 | 0.05 | 5.395 | 0.077 | 0.9704 |

## Temporal locality

| subtype | k | n points | median neighbors | median random | median ratio | mean neighbors | mean random |
|---|---:|---:|---:|---:|---:|---:|---:|
| H1N1 | 5 | 36,753 | 2.00 | 43.00 | 0.047 | 5.29 | 53.93 |
| H1N1 | 10 | 36,753 | 2.00 | 42.00 | 0.048 | 6.34 | 53.66 |
| H1N1 | 20 | 36,753 | 2.00 | 42.00 | 0.048 | 7.60 | 53.66 |
| H3N2 | 5 | 45,553 | 2.00 | 35.00 | 0.057 | 5.09 | 49.01 |
| H3N2 | 10 | 45,553 | 2.00 | 35.00 | 0.057 | 5.98 | 49.10 |
| H3N2 | 20 | 45,553 | 2.00 | 35.00 | 0.057 | 7.18 | 49.05 |

## Figures

- `figures/latent_geometry_full/records_by_year_subtype.pdf`
- `figures/latent_geometry_full/sequence_length_distributions.pdf`
- `figures/latent_geometry_full/spearman_latent_vs_distances.pdf`
- `figures/latent_geometry_full/pca_scree_global.pdf`
- `figures/latent_geometry_full/pca_cumulative_global.pdf`
- `figures/latent_geometry_full/pca_scree_by_subtype.pdf`
- `figures/latent_geometry_full/pca_cumulative_by_subtype.pdf`
- `figures/latent_geometry_full/pca_2d_by_subtype.pdf`
- `figures/latent_geometry_full/pca_2d_by_year.pdf`
- `figures/latent_geometry_full/twonn_sensitivity.pdf`
- `figures/latent_geometry_full/twonn_fit_example.pdf`
- `figures/latent_geometry_full/temporal_local_neighbors_h1n1_dedup.pdf`
- `figures/latent_geometry_full/temporal_local_neighbors_h3n2_dedup.pdf`

## Methodological reading

- Strong Hamming correlations support molecular organization of the local checkpoint embeddings.
- Weak global temporal correlation is not a failure mode by itself, because influenza evolution is branching and nonlinear.
- Strong temporal locality indicates that latent neighborhoods are evolutionarily coherent at local scale.
- Low PCA/TwoNN effective dimension motivates reduced dynamical modeling, but does not validate forecasting or a full SDE.
