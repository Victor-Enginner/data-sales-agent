# CLAUDE.md — data-sales-agent

Pipeline local-first (sem Vercel/Netlify): **Dados → E-book → Landing → Relatório**.

## Comandos
```bash
node main.js                  # pipeline completo
node main.js --dry-run        # simula sem escrever nada
node main.js --full-pipeline  # varredura real
node serve-local.js           # serve output/ em :4173 (http nativo, zero deps)
npm run scrape|generate|build # módulos avulsos
```

## Estrutura
- `modules/` — dataCollector, contentGenerator, landingBuilder, autoPublisher, reportGenerator
- `config/default.js` — nicho atual (Dados de Imóveis SP), `deploy.platform: "local"`
- `output/` — **versionado de propósito** (é o produto servido): dataset_limpo.{json,csv}, guia_tecnico.md, index.html, index-standalone.html, relatorio_final.json

## Regras
- Nenhuma chave hardcoded — se um módulo precisar de API key, usar env/var.
- O output é gerado; pode ser regenerado a qualquer momento (não editar na mão o que o pipeline gera).
- Integrado com `../fabrica-renda-ia` (pilar "datasets" delega pra cá com `../data-sales-agent/main.js` — caminho relativo, não mover a pasta).

## Repo
GitHub: `Victor-Enginner/data-sales-agent` · branch `main`.
