# Diagramas de Costes — TFM SLM

Compilar con **lualatex** (no pdflatex):
```
lualatex cost_comparison_bar.tex
```

## Archivos

### `cost_comparison_bar.tex`
Gráfica de barras: coste real vs Chinchilla-optimal en instancia final.
- Actual: $122 · 713M tokens · 15 épocas · 34,5h
- Chinchilla-optimal: $571 · 3.340M tokens · ~70 épocas · 161,4h
- Instancia: g7e.2xlarge · $3,54/h · RTX PRO 6000

Labels bajo barras: nodos manuales con `\usetikzlibrary{calc}` + `(costaxis.south west)!frac!(costaxis.south east)`.
Fracciones: Actual=0.237, Chinchilla=0.763 (enlarge x limits=0.45, 2 barras).
Nota instancia: `below=2cm` desde `costaxis.south`.

### `cost_cycles_bar.tex`
Gráfica de barras: coste por ciclo de entrenamiento (3 GPUs).
- Ciclo 1: $40 · NVIDIA L4 · g6.2xlarge · $1,03/h
- Ciclo 2: $60 · NVIDIA L40S · g6e.2xlarge · $2,36/h
- Ciclo 3: $122 · RTX PRO 6000 · g7e.2xlarge · $3,54/h

`xticklabels={, , }` vacíos — labels como nodos manuales (multiline con `\\` en xticklabels no funciona).
Fracciones: 0.206 / 0.50 / 0.794 (enlarge x limits=0.35, 3 barras).
Width=13cm para evitar solapamiento.

### `cost_scaling.tex`
Gráfica de línea: escalado lineal de coste en g7e.2xlarge.
- Tasa: $0.171/M tokens (= 122/713)
- Puntos anotados: Real (713M, $122) y Chinchilla (3340M, $571)
- Consistente con `cost_comparison_bar.tex`.

### `cost_total_pie.tex`
Gráfica de tarta: desglose total de costes.

## Valores clave (consistentes entre diagramas)
| Concepto | Valor |
|---|---|
| Coste real | $122 |
| Coste Chinchilla-optimal | $571 |
| Tokens reales | 713M |
| Tokens Chinchilla | 3.340M |
| Instancia final | g7e.2xlarge |
| Precio instancia final | $3,54/h |
