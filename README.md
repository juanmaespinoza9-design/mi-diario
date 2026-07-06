# Mi Diario

Diario personal automatizado: una página estática (GitHub Pages) con los artículos más importantes de mis intereses — Cardiología, Deportes, Ciencia de datos e IA, Argentina e Internacional.

## Cómo funciona

- **Titulares** (`data/articles.json`): un GitHub Action (`.github/workflows/refresh.yml`) corre `scripts/fetch_feeds.py` cada 2 horas. Lee las fuentes definidas en `feeds.yaml` (RSS, PubMed, Google News), deduplica y ordena por fecha.
- **Curaduría** (`data/summaries.json`): un agente programado de Claude Code pasa dos veces por día y escribe resúmenes en español de los artículos de Cardiología y Ciencia de datos, marcando un destacado por sección.
- **La página** (`index.html`): estática, lee los dos JSON. Marca leídos y novedades con localStorage del navegador.

## Editar fuentes

Todo en `feeds.yaml` — agregar o sacar feeds no requiere tocar código. Tipos soportados: `rss`, `pubmed` (query de PubMed) y `googlenews` (búsqueda en Google News, con `locale: ar` o `us`).

## Correr local

```bash
pip3 install -r requirements.txt
python3 scripts/fetch_feeds.py
python3 -m http.server 8000   # abrir http://localhost:8000
```
