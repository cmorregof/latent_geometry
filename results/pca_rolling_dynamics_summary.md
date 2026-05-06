# Rolling-origin dynamics in PCA space

Fuente: `results/embeddings_cache_10k_per_subtype_seed42.pkl`.
No se recalcularon embeddings, no se cargo AntigenLM y no se generaron secuencias.

## Diferencias frente al piloto anterior

- El piloto anterior ajustaba PCA una sola vez sobre todo el cache.
- Esta evaluacion ajusta PCA nuevamente en cada corte, usando solo datos disponibles hasta el mes anterior al objetivo.
- La evaluacion es one-step retrospectiva sobre meses 2019-2022 con centroides mensuales.
- Ridge alpha = 1.0.

## Resultados por modelo

| dim | subtipo | modelo | n eval | RMSE | MAE | distancia euclidiana media | RMSE/persistence | mejora vs persistence | mean loglik RW | NLL media RW |
|---:|---|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 3 | H1N1 | persistence | 29 | 0.0883 | 0.0519 | 0.1153 | 1.0000 | 0.0000 | NA | NA |
| 3 | H1N1 | constant_velocity | 29 | 0.1198 | 0.0791 | 0.1725 | 1.3574 | -0.3574 | NA | NA |
| 3 | H1N1 | ridge_var1 | 29 | 0.0987 | 0.0697 | 0.1396 | 1.1185 | -0.1185 | NA | NA |
| 3 | H1N1 | ridge_var2 | 29 | 0.1002 | 0.0668 | 0.1427 | 1.1348 | -0.1348 | NA | NA |
| 3 | H1N1 | gaussian_rw_mean | 29 | 0.0887 | 0.0522 | 0.1160 | 1.0050 | -0.0050 | 2.9563 | -2.9563 |
| 4 | H1N1 | persistence | 29 | 0.0769 | 0.0414 | 0.1164 | 1.0000 | 0.0000 | NA | NA |
| 4 | H1N1 | constant_velocity | 29 | 0.1049 | 0.0641 | 0.1747 | 1.3632 | -0.3632 | NA | NA |
| 4 | H1N1 | ridge_var1 | 29 | 0.0850 | 0.0549 | 0.1384 | 1.1050 | -0.1050 | NA | NA |
| 4 | H1N1 | ridge_var2 | 29 | 0.0871 | 0.0524 | 0.1434 | 1.1316 | -0.1316 | NA | NA |
| 4 | H1N1 | gaussian_rw_mean | 29 | 0.0773 | 0.0416 | 0.1171 | 1.0050 | -0.0050 | 5.2710 | -5.2710 |
| 5 | H1N1 | persistence | 29 | 0.0695 | 0.0362 | 0.1183 | 1.0000 | 0.0000 | NA | NA |
| 5 | H1N1 | constant_velocity | 29 | 0.0952 | 0.0563 | 0.1782 | 1.3701 | -0.3701 | NA | NA |
| 5 | H1N1 | ridge_var1 | 29 | 0.0762 | 0.0463 | 0.1395 | 1.0975 | -0.0975 | NA | NA |
| 5 | H1N1 | ridge_var2 | 29 | 0.0784 | 0.0446 | 0.1451 | 1.1284 | -0.1284 | NA | NA |
| 5 | H1N1 | gaussian_rw_mean | 29 | 0.0698 | 0.0364 | 0.1190 | 1.0050 | -0.0050 | 7.4956 | -7.4956 |
| 3 | H3N2 | persistence | 32 | 0.0964 | 0.0589 | 0.1346 | 1.0000 | 0.0000 | NA | NA |
| 3 | H3N2 | constant_velocity | 32 | 0.1673 | 0.1019 | 0.2356 | 1.7345 | -0.7345 | NA | NA |
| 3 | H3N2 | ridge_var1 | 32 | 0.0851 | 0.0623 | 0.1308 | 0.8829 | 0.1171 | NA | NA |
| 3 | H3N2 | ridge_var2 | 32 | 0.0822 | 0.0580 | 0.1255 | 0.8526 | 0.1474 | NA | NA |
| 3 | H3N2 | gaussian_rw_mean | 32 | 0.0966 | 0.0590 | 0.1348 | 1.0018 | -0.0018 | 3.0113 | -3.0113 |
| 4 | H3N2 | persistence | 32 | 0.0866 | 0.0517 | 0.1398 | 1.0000 | 0.0000 | NA | NA |
| 4 | H3N2 | constant_velocity | 32 | 0.1504 | 0.0882 | 0.2433 | 1.7372 | -0.7372 | NA | NA |
| 4 | H3N2 | ridge_var1 | 32 | 0.0767 | 0.0544 | 0.1363 | 0.8863 | 0.1137 | NA | NA |
| 4 | H3N2 | ridge_var2 | 32 | 0.0739 | 0.0508 | 0.1305 | 0.8530 | 0.1470 | NA | NA |
| 4 | H3N2 | gaussian_rw_mean | 32 | 0.0867 | 0.0518 | 0.1401 | 1.0018 | -0.0018 | 3.6891 | -3.6891 |
| 5 | H3N2 | persistence | 32 | 0.0793 | 0.0453 | 0.1431 | 1.0000 | 0.0000 | NA | NA |
| 5 | H3N2 | constant_velocity | 32 | 0.1381 | 0.0775 | 0.2490 | 1.7412 | -0.7412 | NA | NA |
| 5 | H3N2 | ridge_var1 | 32 | 0.0691 | 0.0467 | 0.1378 | 0.8712 | 0.1288 | NA | NA |
| 5 | H3N2 | ridge_var2 | 32 | 0.0670 | 0.0437 | 0.1332 | 0.8452 | 0.1548 | NA | NA |
| 5 | H3N2 | gaussian_rw_mean | 32 | 0.0794 | 0.0454 | 0.1434 | 1.0018 | -0.0018 | 4.7830 | -4.7830 |

## Mejor modelo por subtipo

| subtipo | dim | modelo | RMSE | mejora vs persistence |
|---|---:|---|---:|---:|
| H1N1 | 5 | persistence | 0.0695 | 0.0000 |
| H3N2 | 5 | ridge_var2 | 0.0670 | 0.1548 |

## Meses evaluados

| subtipo | dim | targets | primer target | ultimo target | targets omitidos |
|---|---:|---:|---|---|---:|
| H1N1 | 3 | 29 | 2019-01 | 2022-02 | 0 |
| H1N1 | 4 | 29 | 2019-01 | 2022-02 | 0 |
| H1N1 | 5 | 29 | 2019-01 | 2022-02 | 0 |
| H3N2 | 3 | 32 | 2019-01 | 2022-02 | 0 |
| H3N2 | 4 | 32 | 2019-01 | 2022-02 | 0 |
| H3N2 | 5 | 32 | 2019-01 | 2022-02 | 0 |

## Figuras

- `figures/gisaid/pca_rolling_rmse_by_model.png`
- `figures/gisaid/pca_rolling_rmse_by_model.pdf`
- `figures/gisaid/pca_rolling_relative_improvement.png`
- `figures/gisaid/pca_rolling_relative_improvement.pdf`
- `figures/gisaid/pca_rolling_predictions_h1n1_d3.png`
- `figures/gisaid/pca_rolling_predictions_h1n1_d3.pdf`
- `figures/gisaid/pca_rolling_predictions_h3n2_d3.png`
- `figures/gisaid/pca_rolling_predictions_h3n2_d3.pdf`

## Interpretacion prudente

- Persistence sigue siendo un baseline fuerte si las mejoras relativas son pequenas o negativas.
- Constant velocity puede empeorar cuando los incrementos mensuales no son persistentes o hay sobreoscilacion.
- Ridge VAR(1)/VAR(2) solo aporta senal dinamica si mejora persistence de forma estable por subtipo y dimension.
- La senal dinamica puede ser subtipo-dependiente; no debe promediarse sin revisar H1N1 y H3N2 por separado.
- Esto sigue siendo dinamica en PCA space, no una SDE final ni una evaluacion de generacion de secuencias.
