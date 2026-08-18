# prestitonesto · funnel Cessione del Quinto (prototipo)

Due prototipi funzionanti del funnel di qualificazione lead, stesse regole e stessi eventi. Nessuna dipendenza, nessun invio reale di dati (il lead finisce nella console del browser).

- `corto/` · landing + quiz in 4 step (variante A). Mappa: `MAPPA_CORTO.md`
- `lungo/` · ricostruzione della reference, CAP + 9 step (variante B). Mappa: `MAPPA_FUNNEL.md`
- `index.html` · pagina indice per scegliere

- **Demo online:** https://tom-pier.github.io/prestitonesto-funnel-cdq/ (corto: `/corto/`, lungo: `/lungo/`)
- **Mappa del corto:** [`MAPPA_CORTO.md`](MAPPA_CORTO.md) · **Mappa del lungo:** [`MAPPA_FUNNEL.md`](MAPPA_FUNNEL.md)
- **Note di ricostruzione rispetto al riferimento:** [`RICOSTRUZIONE.md`](RICOSTRUZIONE.md)

## Provarlo in locale

```bash
python3 -m http.server 8765
# poi apri http://localhost:8765
```

## Parametri

Tutte le soglie (reddito minimo, età massima, dipendenti, anzianità, rinnovi, SLA di richiamo, esempio rappresentativo, endpoint) sono nel blocco `CFG` in testa a `corto/index.html` e `lungo/index.html`.

Documento di lavoro Performance Boutique. I testi di conformità (footer, informativa) sono placeholder da completare con ragione sociale, iscrizione OAM e mandante.
